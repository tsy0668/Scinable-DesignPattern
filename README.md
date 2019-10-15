# Head First Design Patterns

## 개요
Practice and description design patterns using Java - Working in Scinable(Overseas Internship)
## 목차
### 객체지향 원칙
### 1. Strategy Pattern
### 2. Observer Pattern
### 3. Decorator Pattern
### 4. Factory pattern
***
### 객체지향 원칙
-	바뀌는 부분은 캡슐화한다.
-	상속보다는 구성을 활용한다.
-	구현이 아닌 인터페이스에 맞춰서 프로그래밍한다.
-	서로 상호작용을 하는 객체 사이에서는 가능하면 느슨하게 결합하는 디자인을 사용해야 한다.
-	클래스는 확장에 대해서는 열려 있지만 변경에 대해서는 닫혀 있어야 한다.
-	추상화된 것에 의존하라. 구상 클래스에 의존하지 않도록 한다.
***
### 1. Strategy Pattern
#### 스트래티지 패턴 (Strategy Pattern)
스트래티지 패턴에서는 알고리즘군을 정의하고 각각을 캡슐화하여 교환해서 사용할 수 있도록 만든다. 스트래티지를 활용하면 알고리즘을 사용하는 클라이언트와는 독립적으로 알고리즘을 변경할 수 있다.
#### 디자인 원칙
애플리케이션에서 달라지는 부분을 찾아내고 달라지지 않는 부분으로부터 분리시킨다.  
바뀌는 부분은 따로 뽑아서 캡슐화시킨다. 그렇게 하면 나중에 바뀌지 않는 부분에는 영향을 미치지 않은 채로 그 부분만 고치거나 확장할 수 있다.  
상속보다는 구성을 이용한다.   
구현이 아닌 인터페이스(상위형식)에 맞춰서 프로그래밍한다.
*	구현에 맞춰서 프로그래밍 (X)  
 Dog d = new Dog(); 
d.bark();
*	인터페이스/상위형식에 맞춰서 프로그래밍 (Δ)  
 Animal animal = new Dog(); 
animal.makeSound();
*	구체적으로 구현된 객체를 실행시에 대입 (O)  
 a = getAnimal();
 a.makeSound();
#### 객체지향의 기초
추상화  
캡슐화  
다형성  
상속
#### 객체지향 원칙
바뀌는 부분은 캡슐화한다.  
상속보다는 구성을 활용한다.  
구현이 아닌 인터페이스에 맞춰서 프로그래밍 한다.
***
### 2. Observer Pattern
#### 옵저버 패턴 (Observer Pattern)
한 객체의 상태가 바뀌면 그 객체에 의존하는 다른 객체들한테 연락이 가고 자동으로 내용이 갱신되는 방식으로 일대다(one-to-many) 의존성을 정의한다. 일대다 관계는 주제(Subject)와 옵저버(Observer)에 의해 정의된다. 옵저버는 주제에 의존한다. 주제의 상태가 바뀌면 옵저버한테 연락이 가고 연락 방법에 따라 옵저버에 있는 값이 새로운 값으로 갱신될 수 있다.  
#### 디자인 원칙
옵저버 패턴을 구현하는 방법에는 여러가지가 있지만, 대부분 주제(Subject)인터페이스와 옵저버(Observer)인터페이스가 들어있는 클래스 디자인을 바탕으로 한다.  
주제 역할을 하는 구상 클래스에서는 항상 Subject 인터페이스를 구현해야 한다.  
Observer 인터페이스만 구현한다면 무엇이든 옵저버 클래스가 될 수 있다.  
서로 상호작용을 하는 객체 사이에서는 가능하면 느슨하게 결합하는 디자인을 사용해야 한다. 느슨하게 결합하는 디자인을 사용하면 변경 사항이 생겨도 무난히 처리할 수 있는 유연한 객체지향 시스템을 구축할 수 있다.
#### 핵심정리
옵저버 패턴에서는 객체들 사이에 일대다 관계를 정의한다.  
주제, 또는 Observable 객체는 동일한 인터페이스를 써서 옵저버에 연락한다.  
Observerble에서는 옵저버들이 Observer 인터페이스를 구현한다는 것을 제외하면 옵저버에 대해 전혀 모르기 때문에, 이들 사이의 결합은 느슨한 결합이다.  
옵저버들한테 연락을 돌리는 순서에 절대 의존하면 안된다.  
자바에서는 범용으로 쓸 수 있는 java.util.Observable을 비롯하여 옵저버 패턴을 구현한 것들이 여럿 있다. Observable은 인터페이스가 아니라 클래스이기 때문에 "확장"해야한다.


***
### 3. Decorator Pattern

#### 데코레이터 패턴(Decorator Pattern)
객체에 추가적인 요건을 동적으로 첨가한다. 데코레이터는 서브클래스를 만드는 것을 통해서 기능을 유연하게 확장할 수 있는 방법을 제공한다.

#### OCP(Open-Closed Principle)
(데코레이터 패턴은 OCP에 충실)  
: 클래스는 확장에 대해서는 열려 있어야 하지만 코드 변경에 대해서는 닫혀 있어야 한다.  
무조건 OCP를 적용하면 오히려 불필요하게 복잡하고 이해하기 힘든 코드만 만들게 되는 부작용이 있을 수 있다.  코드가 바뀔 가능성이 있는 부분을 잘 뽑아내서 OCP를 준수한다.

#### 핵심정리
구성과 위임을 통해서 실행중에 새로운 행동을 추가할 수 있다.  
상속 대신 데코레이터 패턴을 통해서 행동을 확장할 수 있다.  
데코레이터 패턴에서는 구상 구성요소를 감싸주는 데코레이터를 사용한다.  
데코레이터 클래스의 형식은 그 클래스가 감싸고 있는 클래스의 형식을 반영한다. (상속 또는 인터페이스 구현을 통해서 자신이 감쌀 클래스와 같은 형식을 가지게 된다.)  
데코레이터에서는 자기가 감싸고 있는 구성요소의 메소드를 호출한 결과에 새로운 기능을 더함으로써 행동을 확장한다.  
구성요소를 감싸는 데코레이터의 개수제한은 없다.  
구성요소의 클라이언트 입장에서는 데코레이터의 존재를 알 수 없다. (클라이언트에서 구성요소의 구체적인 형식에 의존하게 되는 경우 예외)  
Java.io.API 문서도 데코레이터 패턴으로 구성  
데코레이터 패턴을 이용해서 디자인하다 보면 잡다한 클래스들이 너무 많아진다. 하지만 데코레이터가 어떤 식으로 작동하는지 이해하고 나면, 다른 사람이 데코레이터 패턴을 활용해서 만든 API를 쓰더라도 클래스들이 어떤 식으로 구성되어 있는지 일단 파악하고 나면 클래스를 데코레이터로 감싸서 원하는 행동을 구현할 수 있다.  
객체지향 원칙 : 클래스는 확장에 대해서는 열려 있지만 변경에 대해서는 닫혀 있어야 한다. 
***
### 4. Factory pattern

#### 팩토리(Factory)
객체 생성을 처리하는 클래스를 팩토리(Factory)라고 부른다.

#### 객체를 생성하는 코드 캡슐화 
구상 클래스의 인스턴스를 만드는 코드가 있다면 그 부분은 쉽게 바뀔 수 있다. 그러므로 인스턴스를 만드는 행동을 캡슐화한다.(팩토리) 

#### 팩토리 메소드 패턴 (Factory Method Pattern)
팩토리 메소드 패턴에서는 객체를 생성하기 위한 인터페이스를 정의하는데, 어떤 클래스의 인스턴스를 만들지는 서브클래스에서 결정하게 만든다.

#### 간단한 팩토리와 팩토리 메소드 패턴의 차이점
간단한 팩토리는 일회용 처방에 불과한 반면, 팩토리 메소드 패턴을 이용하면 어떤 구현을 사용할지를 서브클래스에서 결정하는 프레임워크를 만들 수 있다.  
+ 객체 생성 코드를 한 객체 또는 메소드에 집어넣으면 코드에서 중복되는 내용을 제거할 수 있고 관리도 용이하다. 클라이언트 입장에서 객체 인스턴스를 만들 때 필요한 구상 클래스가 아닌 인터페이스만 필요로 하게 된다. – 유연성과 확장성 증진

#### 의존성 뒤집기 원칙 (Dependency Inversion Principle)
추상화된 것에 의존하도록 만든다. 구상 클래스에 의존하도록 만들지 않도록 한다.  
- 저수준 모듈과 고수준 모듈 모두 추상 클래스에 의존  
1. 어떤 변수에도 구상 클래스에 대한 레퍼런스를 저장하지 말기 – new 연산자를 사용하면 구상 클래스에 대한 레퍼런스를 사용하게 되는 것이다. 그러므로 팩토리를 써서 구상 클래스에 대한 레퍼런스를 변수에 저장하는 일을 미리 방지한다.  
2. 구상 클래스에서 유도된 클래스를 만들지 말기 – 구상 클래스에서 유도된 클래스를 만들면 특정 구상 클래스에 의존하게 된다. 인터페이스나 추상 클래스처럼 추상화된 것으로부터 클래스를 만들어야 한다.  
3. 베이스 클래스에 이미 구현되어 있던 메소드를 오버라이드 하지 말기 – 이미 구현되어 있는 메소드를 오버라이드한다는 것은 애초부터 베이스 클래스가 제대로 추상화 된 것이 아니다. 베이스 클래스에서 메소드를 정의할 때는 모든 서브클래스에서 공유할 수 있는 것만 정의해야 한다.

#### 추상 팩토리 패턴
추상 팩토리 패턴에서는 인터페이스를 이용하여 서로 연관된, 도는 의존하는 객체를 구상 클래스를 지정하지 않고도 생성할 수 있다

#### 핵심정리
팩토리를 쓰면 객체 생성을 캡슐화 할 수 있다.  
간단한 팩토리는 엄밀하게 디자인 패턴은 아니지만, 클라이언트와 구상 클래스를 분리시키기 위한 간단한 기법으로 활용할 수 있다.  
팩토리 메소드 패턴에서는 상속을 활용한다. 객체 생성이 서브클래스에게 위임된다. 서브클래스에서는 팩토리 메소드를 구현하여 객체를 생산한다.  
추상 팩토리 패턴에서는 객체 구성을 활용한다. 객체 생성이 팩토리 인터페이스에서 선언한 메소드들에서 구현된다.  
모든 팩토리 패턴에서는 애플리케이션의 구상 클래스에 대한 의존성을 줄여줌으로써 느슨한 결합을 도와준다.  
팩토리 메소드 패턴에서는 어떤 클래스에서 인스턴스를 만드는 일을 서브클래스한테 넘긴다.  
추상 팩토리 패턴은 구상 클래스에 직접 의존하지 않고도 서로 관련된 객체들로 이루어진 제품군을 만들기 위한 용도로 쓰인다.  
의존성 뒤집기 원칙을 따르면 구상 형식에 대한 의존을 피하고 추상화를 지향할 수 있다.  
팩토리는 구상 클래스가 아닌 추상 클래스/인터페이스에 맞춰서 코딩할 수 있게 해주는 강력한 기법이다.  
객체지향 원칙 : 추상화된 것에 의존하라. 구상 클래스에 의존하지 않도록 한다.  




