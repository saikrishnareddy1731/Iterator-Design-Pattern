# Iterator Design Pattern in Java

## Overview

The **Iterator Pattern** is a **behavioral design pattern** that provides a way to access the elements of a collection sequentially **without exposing its underlying representation** (array, list, tree, etc.).

---

## Key Points

- Provides a **standard way to traverse collections**.
- Encapsulates iteration logic in a separate **Iterator object**.
- Decouples the collection from the traversal process.

---

## Real-world Analogy

Think of a **remote control for a TV**:  
- You don’t need to know how the channels are stored internally.  
- You just press **Next / Previous** to move through them.  
- The **Iterator** plays the role of the remote control for navigating a collection.

---

## Components

1. **Iterator Interface** → Defines methods for iteration.  
   Example: `Iterator<T>`

2. **Concrete Iterator** → Implements iteration logic.  
   Example: `NameIterator`

3. **Aggregate (Collection) Interface** → Provides a method to create an iterator.  
   Example: `Container`

4. **Concrete Aggregate** → Implements collection storage and returns an iterator.  
   Example: `NameRepository`

5. **Client** → Uses the iterator to traverse the collection.  
   Example: `Main`

---

## UML Diagram

```mermaid
classDiagram
    direction LR

    Iterator <|.. NameIterator
    Container <|.. NameRepository
    NameRepository --> NameIterator : creates
    Main --> Container : uses
    Main --> Iterator : traverses

    class Iterator {
        <<interface>>
        +boolean hasNext()
        +Object next()
    }

    class Container {
        <<interface>>
        +Iterator getIterator()
    }

    class NameIterator {
        -int index
        +boolean hasNext()
        +Object next()
    }

    class NameRepository {
        -String[] names
        +Iterator getIterator()
    }

    class Main {
        +main()
    }
