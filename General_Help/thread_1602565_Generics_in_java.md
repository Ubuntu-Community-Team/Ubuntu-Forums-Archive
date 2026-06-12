---
title: "Generics in java"
date: 2010-10-21
forum: General Help
---

### Post by pookie9 on 2010-10-21
So I'm doing some work in java, and I made the following class declaration:

public class Heap<E extends Comparable>

And I received the following error:

ERROR in Heap.java (at line 1)
    public class Heap<E extends Comparable>
                      ^^^^^^^^^^^^^^^^^^^^
Syntax error, type parameters are only available if source level is 1.5


I have the most up to date java, 1.6.0_18 and this is obviously a valid class declaration, so what's the problem?

---

### Post by lykeion on 2010-10-21
> **pookie9 said:**
> 
Syntax error, type parameters are only available if source level is 1.5
This is the clue...try setting the source level to 1.5 (i.e support generics) or higher when you compile:
```
javac -source 1.5 Heap.java
```
If you're using an IDE set this at project properties. In IntelliJ Idea the settings is called "Project language level". In Eclipse it's called "Compiler compliance level".
Hope it helps...

---

### Post by QIII on 2010-10-21
And, by the way, Java is up to Update 22.

---

