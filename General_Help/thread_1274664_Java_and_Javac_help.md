---
title: "Java and Javac? help"
date: 2009-09-24
forum: General Help
---

### Post by ductiletoaster on 2009-09-24
Ok so i have an assignment i have to do for this class. Well basically we have to compile and execute it and its supposed to print some stuff out before we continue development. 

Now our prof and all the students (Sep me) are using Windows of some kind...ewww jk. Im of course using Ubuntu 9.04 64bit. And so far havent had any problems. till now!

to compile our professor wants us to use this cmd
```

javac -cp twitter4j.jar;. assignment5.java

```
This doesnt work so i tired this
```

javac -cp twitter4j.jar assignment5.java

```
only diff is the lack of ;. and this works and creates a .class file!!!

so then she gives us this cmd to run it...
```

java -cp twitter4j.jar;. assignment5

```
THis doesnt work... i have also tried replacing the -cp with -classpath and i get the same resualts. I have tried so many different things that im not goin to bother listing them all so if any one can help me determine the right cmds to run this i would appreciate this! thanks

---

### Post by ductiletoaster on 2009-09-24
Here is the answer i figured it out with the help of my prof!
```
java -cp twitter4j.jar:. assignment5
```

use a : instead of a ;

---

