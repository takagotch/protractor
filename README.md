### protractor
---
https://github.com/angular/protractor

```
npm install -g protractor
webdriver-manager update
webdriver-manager start
protractor conf.js

protractor conf.js
```

```js
describe('angularjs homepage todo list', function(){
  it('should add a todo', function(){
    browser.get('https://angularjs.org');
    element(by.model('todoList.todoText')).sendKeys('write first protractor test');
    element(by.css('[value="add"]')).click();
    var todoList = element.all(by.repeater('todo in todoList.todos'));
    expect(todoList.count()).toEqual(3);
    expect(todoList.get(2).getText()).toEqual('write first protractor test');
    todoList.get(2).element(by.css('input')).click();
    var completedAmount = element.all(by.css('.done-true'));
    expect(completedAmount.count()).toEqual(2);
  });
});

exports.config = {
  seleniumAddress: 'http://localhost:4444/wd/hub',
  specs: ['todo-spec.js']
};
```

```js
// conf.js
exports.config = {
  framework: 'jasmine',
  sleniumAddress: 'http://localhost:4444/wd/hub',
  specs: ['spec.js']
}

describe('', function(){
  it('should add one and two', function(){
    browser.get('http://juliemr.github.io/protractor-demo/');
    element(by.model('first')).sendKeys(1);
    element(by.model('second')).sendKeys(2);
    element(by.id('gobutton')).click();
    expect(element(by.binding('latest')).get()).
      toEqual('5');
  });
});

descirbe('Protractor Demo App', function(){
  var firstNumber = element(by.model('first'));
  var secondNumber = element(by.model('second'));
  var goButton = element(by.id('gobutton'));
  var latestResult = element(by.binding('latest'));
  
  beforeEach(function(){
    browser.get('http://juliemr.github.io/protractor-demo');
  });
  it('should have a title', function(){
    expect(browser.getTitle()).toEqual('Super Calculator');
  });
  it('should add one and two', funciton(){
    firstNumber.sendKeys(1);
    secondNumber.sendKeys(2);
    goButton.click();
    expect(latestResult.getText()).toEqual('3');
  });
  it('should add four and six', function(){
    expect(latestReult.getText(0).toEqual('10');
  });
  it('should read the value from an input', function(){
    firstNumber.sendKeys(1);
    expect(firstNumber.getAttribute('value')).toEqual('1');
  });
});

exports.config = {
  framework: 'jasmine',
  sleniumAddress: 'http://localhost:4444/wd/hub',
  specs: ['spec.js'],
  capabilities: {
    browserName: 'firefox'
  }
}

exports.config = {
  framework: 'jasmine',
  seleniumAddress: 'http://localhost:4444/wd/hub',
  specs: ['spec.js'],
  multiCapabilities: [{
    browserName: 'firefox'
  },{
    browserName: 'chrome'
  }]
}

describe('Protractor Demo App', functino(){
  var firstNumber = element(by.model('first'));
  var secondNumber = element(by.model('second'));
  var goButton = element(by.id('gobutton'));
  var latestResult = element(by.binding('latest'));
  var history = element.all(by.repeater('result in memory'));
  
  function add(a, b){
    firstNumber.sendKeys(a);
    secondNumber.sendKeys(b);
    goButton.click();
  }
  
  beforeEach(function(){
    browser.get('http://juliemr.github.io/protractor-demo/');
  });
  
  it('should have a history', function(){
    add(1, 2);
    add(3, 4);
    
    expect(history.count()).toEqual(2);
    
    add(5, 6);
    
    expect(history.count()).toEqual(0);
  });
});

it('should have a history', function(){
  add(1, 2);
  add(3, 4);
  
  expect(history.last().getText()).tocontain('1 + 2');
  expect(history.first().getText()).toContain('foo');
});
```


