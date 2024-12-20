# Clean Architecture - Robert C. Martin

This is another book I read in the clean series by Robert C. Martin.

This book describes what good, clean architectures and designs look like so that software developers can build systems that will have long, profitable lifetimes.

Chapter 1 [What is Design and Architecture?] explains the difference between design and architecture.

- For starters, there is no difference between design and architecture.
- Architecture is at a high level, and design implies structures and decisions at a lower level.
- This may sound nonsensical as you can't have one without the other; indeed, no clear dividing line separates them. There is simply a continuum of decisions from the highest to the lowest levels.
- RCM: The goal of software architecture is to minimize the human resources required to build and maintain the required system.
- To take software architecture seriously, you need to know what good software architecture is. To build a system with a design and an architecture that minimizes effort and maximizes productivity, you need to know which attributes of the system architecture lead to that end.

Chapter 2 [A Tale of Two Values] - 

- Every software system must provide two different values to the stakeholders: behavior and structure. Unfortunately, software developers focus on one to the exclusions of the other.

  - **Behavior**: Functional specs and requirements document the software behavior. Many programmers believe that implementing these requirements and fixing any bugs is their job. They are sadly mistaken.

  - **Architecture:** Software must be easy to change. The difficulty in making a change should be proportional only to the scope of the change and not to the shape of the change. 

  - The first value of software, behavior, is urgent but not always particularly important.

  - The second value of software, architecture, is important but never particularly urgent.

  - Eisenhower's matrix of importance vs urgency says that the urgent are unimportant, and important is never urgent.

  - | 1<br />IMPORTANT<br />URGENT                 | 2<br />IMPORTANT<br />NOT URGENT               |
    | -------------------------------------------- | ---------------------------------------------- |
    | **3*<br />*****UNIMPORTANT**<br />**URGENT** | **4**<br />**UNIMPORTANT**<br />**NOT URGENT** |

  - Architecture is 1 and 2

  - Behavior is 1 and 3

  - As software developers and architects, we must try to balance between what is important and urgent. 

Chapter 3 [Paradigm Overview]

- A programming paradigm is a way of programming. It is unrelated to the language. A paradigm tells you which programming structures to use, and when to use them. To date, there have been three such paradigms -- structured, object-oriented, and functional.
- Structured
  - Discovered by Edsger Wybe Dijkstra in 1968
  - He replaced jumps done using goto statements with if/then/else and do/while/until constructs.
  - Structured programming imposes discipline on the direct transfer of control.
- Object-oriented programming
  - Ole Johan Dahl and Kristen Nygaard discovered OOP in 1966
  - By moving the function call stack frame to a heap, local variables can exist long after the function is returned. Function became a constructor for a class, local variables became instance variables, and the nested functions became methods. This led to the discovery of polymorphism.
  - OOP imposes discipline on indirect transfer of control.
- Functional programming
  - This was the first to be invented in 1936 by Alonzo Church and predates computer programming itself.
  - A functional language has no assignment statement as these languages are built on the notion that the values of symbols do not change (l-calculus immutability).
  - FP imposes discipline upon assignment.
- These paradigms remove capabilities from the programmer. None of them adds new capabilities. Each imposes some extra discipline that is negative in its intent. The paradigms tell us what not to do, more than they us what to do.

Paradigms are important to architecture. For ex, we use polymorphism as the mechanism to cross architectural boundaries; we use functional programming to impose discipline on the location of and access to data; and we use structured programming as the algorithmic foundation of our modules. These three align well with three big concerns of architecture -- function, separation of components, and data management.

Chapter 4 [Structured Programming]

- Bohm and Kacopini proved that all programs can be constructed from just three structures: sequence, selection, and iteration.
- The very control structures that made a module provable were the same minimum set of control structures from which all programs can be built. 
- Structured programming allows modules to be recursively decomposed into provable units.
- Software architects strive to define modules, components, and services that are easily falsifiable (testable).

Chapter 5 [Object-Oriented Programming]

- Understanding and application of the principles of OOP is the basis of good architecture.
- OOP is the combination of data and function.
- OOP is a way to model the real world.
- Some use encapsulation, inheritance, and polymorphism to explain OO.
- Encapsulation:
  - OO provides an easy way to encapsulate data and functions. 
- Inheritance:
  - Redeclaration of a group of variables and functions within an enclosing scope. 
- Polymorphism:
  - In C++, every virtual function within a class has a pointer in a table called vtable, and all calls to virtual functions go through that table.
  - Before OO, polymorphism was considered and implemented to be an application of pointers to functions. This is dangerous. 
  - OO makes polymorphism trivial.
- Dependency inversion:
  - In the past, the flow of control was dictated by the behavior of the system, and that flow of control dictated the source code dependencies.
  - OO polymorphism means that any source code dependency, no matter where it is, can be inverted.
  - Allows architects to create a plugin architecture, in which modules that contain high-level policies of independent modules that contain low-level details. The low-level details are relegated to plugin modules that can be deployed and developed independently from those with high-level policies. 

[Chapter 6] - Functional Programming:

- Variables in functional languages do not vary.

SOLID Principles:

- SOLID principles tell us to how to arrange our functions and data structures into classes, and how those classes should be interconnected. A class, in this context, is simply a coupled grouping of functions and data.
- The goal of these principles is the creation of mid-level software structures that:
  - Tolerate change,
  - Are easy to understand, and 
  - are the basis of components that can be used in many software systems

[Chapter 7] - Single Responsibility Principle

- A module should be responsible to one, and only one, actor.
- The word cohesive implies SRP. Cohesion is the force that binds together the code responsible to a single actor.
- Symptoms violating SRP:
  - accidental duplication: occurs because we put the code that different actors depend on into close proximity. The SRP says to separate the code that different actors depend on.
  - Merges: occurs when the code has support for multiple actors.

[Chapter 8] - The Open-Closed Principle:

- A software artifact should be open for extension but closed for modification.
- Architects separate functionality based on how, why, and when it changes, and then organize that separated functionality into a hierarchy of components. Higher-level components in that hierarchy are protected from the changes made to lower-level components.

[Chapter 9] - Liskov Substitution Principle:

- The LSP can, and should, be extended to the level of architecture. A simple violation of substitutability can cause a system's architecture to be polluted with a significant amount of extra mechanisms.

[Chapter 10] - Interface Segregation Principle:

- It is harmful to depend on modules that contain more than you need. 

[Chapter 11] - Dependency Inversion Principle:

- The most flexible systems are those in which source code dependencies refer only to abstractions, not to concretions.

[Chapter 12] - Components:

- Components are units of deployment as a part of a system.
- Component plugin architecture is a casual default today.

[Chapter 13] - Component Cohesion:

- There are three principles of component cohesion.
- Reuse/Release Equivalence principle:
  - The granule of reuse is the granule of release.
- Common Closure Principle:
  - Gather into components those classes that change for the same reasons and at the same time. Separate into different components those classes that change at different times and for different reasons.
  - This is similar to SRP
  - Closely associated with Open-Closed principle
- Common Reuse Principle:
  - Don't force users of a component to depend on things that they don't need.
  - Helps us decide which classes and modules should be placed into a component.
  - The classes and modules that tend to be reused together belong in the same component. CRP also tells us which classes not to keep together in a component.
  - CRP is a generic version of ISP. ISP advises us not to depend on classes that have methods we don't use. The CRP advises us not to depend on components that have classes we don't use.
  - Don't depend on things that you don't need.
- REP and CCP are inclusive principles: both tend to make components larger.
- CRP is exclusive: drives components to be smaller.
- A good architect seeks to resolve the tension between these principles.

[Chapter 14] - Component coupling:

- The forces that impinge upon the architecture of a component structure are technical, political, and volatile.
- Acyclic Dependencies principle:
  - Allow no cycles in the component dependency graph
  - The solution to the longer build and integration problems is to partition the development environment into releasable components. 
  - To make this successful, you need a better dependency structure. There can be no cycles.
  - Component dependency diagrams do not describe the function of the application. Instead, they are a map of the buildability and maintainability of the application. 
- Stable Dependencies Principle:
  - Depend in the direction of stability
  - By conforming to CCP, we create components that are sensitive to certain kinds of changes but immune to others.
  - Any component that we expect to be volatile should not be depended on by a component that is difficult to change. Otherwise, the volatile component will also be difficult to change.
  - SDP ensures that modules that are intended to be easy to change are not depended on by modules that are harder to change.
  - Stability is related to the amount of work required to make a change. 
  - Many factors may make a software component hard to change --size, complexity, clarity, etc. One sure way to make a software component difficult to change is to make lots of other components depend on it.
  - number of dependencies is one measure of stability. fan-out/(fan-in+fan-out); called I metric
  - the I metric of a component should be larger than the I metrics of the components that it depends on. that is, I metrics should decrease in the direction of dependency.
  - I = 0 Stable and I = 1 unstable
- Stable Abstractions Principle:
  - A component should be as abstract as it is stable.
  - SAP sets up a relationship between stability and abstractness.
    - A stable component should also be abstract so that its stability does not prevent it from being extended; a stable component should contain interfaces and abstract classes so that it can be extended.
    - An unstable component should be concrete since its instability allows the concrete code within it to be easily changed.
    - A metric is a measure of the abstractness of a component. It is simply the ratio of interfaces and abstract classes in a component to the number of classes in the component.
    - Nc -> Number of classes; Na -> Number of abstract classes and interfaces
    - A = Na / Nc
    - A == 0 => component has no abstract classes; A == 1 => component has nothing but abstract classes.

[Chapter 15] - What is architecture?

- The architecture of a software system is the shape given to that system
- Every software system has behavior and structure. Software was invented because we needed a way to quickly and easily change the behavior of machines. But that flexibility depends on critically on the shape of the system.
- All software systems can be decomposed into policies and details. the policy is business rules and procedures and details that enable humans, other systems, and programmers to communicate with the policy. Policy is where the true value of the system lives. Details include IO devices, databases, web systems, servers, frameworks, communication protocols, and so forth.
- The form of that shape is in the division of that system into components, the arrangements of those components, and the ways in which those components communicate with each other.
- The purpose of that shape is to facilitate the development, deployment, operation, and maintenance of the software system contained within it.
- A system with terrible architecture may be operational. But, the troubles lie in their deployment, maintenance, and ongoing development.
- The primary purpose of architecture is to support the life cycle of the system. The ultimate goal is to minimize the lifetime cost of the system and to maximize programmer productivity

[Chapter 16] - Independence

- A good architecture must support
  - use cases and operation of the system
  - maintenance of the system
  - development of the system
  - deployment of the system
- Use cases:
  - Architecture must support the intent of the system
  - There are very few behavioral options that the architecture can leave open, and architecture does not wield much influence over the behavior of the system
  - A good architecture can clarify and expose behavior so that the system's intent is visible at the architecture level.
- Operation:
  - Architecture is more substantial and less cosmetic in supporting the system's operation.
- Development:
  - Any organization that designs a system will produce a design whose structure is a copy of the organization's communication structure.
  - Components in a system should be independently developable.
- Deployment:
  - Architecture also determines the ease with which the system is deployed.
- A good architecture balances all these concerns with the component structure that mutually satisfies them all.
- A good architecture makes the system easy to change in all ways that it must change by leaving options open.
- Divide the system into horizontal layers
  - UI
  - Application-specific business rules
  - Application independent business rules
  - The database
  - and so on
- use cases cut through each horizontal layer
  - If you decouple the elements of the system that change for different reasons, then you can continue to add new use cases without interfering with old ones.

[Chapter 17] - Boundaries - Drawing lines:

- Boundaries are drawn where there is an axis of change. The components on one side of the boundary change at different rates and for different reasons than those on the other side of the boundary.
- To draw boundary lines in a system, you first partition the system into components.

[Chapter 18] - Boundary Anatomy

- The architecture of a system is defined by a set of software components and the boundaries that separate them. 
- Most systems, other than monoliths, use more than one boundary strategy. A system that makes use of service boundaries may also have some local process boundaries. 
- The boundaries in a system will often be a mixture of local chatty boundaries and boundaries that are more concerned with latency.

[Chapter 19] - Policy and Level:

- The art of architecture often involves forming the regrouped components into a DAG. The nodes of the DAG are the components that contain policies at the same level. The edges are the dependencies between those components. They connect components that are at different levels.
- We want source code dependencies to be decoupled from data flow and coupled to level.

[Chapter 20] - Business Rules:

- An entity within our computer system embodies a small set of critical business rules operating on critical business data. The interface of the entity consists of the functions that implement the critical business rules that operate on that data.
- A use case is a description of the way that an automated system is used. A use case describes application-specific business rules instead of the critical business rules within entities.
- use cases contain the rules that specify how and when the critical business rules within the entities are invoked. Use cases control the dance of the entities.

[Chapter 21] - Screaming Architecture:

- Software architectures are structures that support the use cases of the system.
- A good architecture allows decisions about frameworks, databases, web servers, and other environmental issues and tools to be deferred and delayed.
- your system architecture should be as ignorant as possible about how it will be delivered.
  - Should be able to deliver it as a console app or a web app, or a thick client app, and even a web service app

[Chapter 22] - Clean Architecture:

- In the clean architecture, the concentric circles represent different areas of software. The further in you go, the higher level the software becomes. The outer circles are mechanisms. The inner circles are policies. 
- The overriding rule that makes this architecture work is the Dependency rule.
  - Source code dependencies must point only inward, towards higher-level policies.

[Chapter 23] - Presenters and Humble Objects:

- The humble object pattern was originally identified to help unit testers separate behaviors that are hard to test from those that are easy to test.
- Testability is an attribute of good architecture. 
- The humble object pattern is a good example because separating the behaviors into testable and non-testable parts often defines an architectural boundary.

[Chapter 24] - Partial Boundaries:

- Full-fledged architectural boundaries are expensive.
- One way to construct a partial boundary is to do all the work necessary to create independently compilable and deployable components and then keep them together in the same component.

[Chapter 25] - Layers and Boundaries:

- As an architect, you must see the future, guess intelligently, weigh the costs, and determine where the architectural boundaries lie, which should be fully implemented, partially implemented, and ignored. 
- This is not a one-time decision. You pay attention as the system evolves. 
- Your goal is to implement the boundaries right at the inflection point where the cost of implementing becomes less than the cost of ignoring.

[Chapter 26] - The main component:

- It is in the main component that dependencies should be injected by a Dependency Injection framework. Once they are injected into Main, Main should distribute those dependencies normally, without using the framework.

[Chapter 27] - Services: Great and small:

- Services may not always be architecturally significant. The architecture of a system is defined by the boundaries drawn within that system, and by the dependencies that cross those boundaries. The system architecture is not defined by the physical mechanisms by which elements communicate and execute.

[Chapter 28] - Test Boundary:

- Tests are a part of the system, and they participate in the architecture just like every other part of the system.
- The first rule of software design is to design for testability.
- The goal should be to decouple of the structure of the tests from the structure of the application.

[Chapter 29] - Clean Embedded Architecture:

- Letting all code become firmware is not good for your product's long-term health. 
- Being able to test only in the target hardware is not good for your product's long-term health

[Chapter 30] - The Database is detail:

- From an architectural point of view, the database is a non-entity -- it is a detail that does not rise to the level of an architectural element.
- Data model is significant to your application architecture; database is not the data model.
- Database is a utility that provides access to the data.
- From an architecture's point of view, the utility is irrelevant because it's a low-level detail -- a mechanism. A good architect does not allow low-level details to pollute the system architecture.

[Chapter 31] - The Web is a Detail:

- The oscillations in the technology are just short-term issues that we want to push away from the central core of our business rules.

[Chapter 32] - Frameworks are details:

- Frameworks are not architectures -- though some try to be.
- The solution is not to marry the framework
- Treat the framework as a detail that belongs in one of the outer circles of the architecture. Don't let it into the inner circles.
- Keep the framework behind an architectural boundary if at all possible, for as long as possible.

[Chapter 33] - Case Study: Video Sales

[Chapter 34] - The missing chapter:

- 