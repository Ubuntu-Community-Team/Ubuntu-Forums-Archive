---
title: "installing java"
date: 2009-07-04
forum: General Help
---

### Post by asliyanage on 2009-07-04
i need to install java to my ubuntu 9.0.
i just type javac in terminal.then it gives this.
"
The program 'javac' can be found in the following packages:
 * openjdk-6-jdk
 * ecj
 * gcj-4.3
 * java-gcj-compat-dev
 * gcj-4.2
 * jikes-classpath
 * jikes-kaffe
 * kaffe
 * sun-java5-jdk
 * sun-java6-jdk
"

where can i find these packages.are they in my computer or is it in ubuntu 9.0 cd.
If i used ubuntu 9.0 DVD instead of ubuntu 9.0 cd is it automatically supply jdk package?

---

### Post by x33a on 2009-07-04
do this:

```
sud aptitude install sun-java6-jre sun-java6-bin sun-java6-plugin
```

---

### Post by asliyanage on 2009-07-04
i did that and it was installed.finally it gives this in my terminal .what should i do?
"
 &#9474;                                                                           &#9474; 
 &#9474;     its subject matter.  It supersedes all prior or contemporaneous       &#8593; 
 &#9474;     oral or written communications, proposals, representations and        &#9618; 
 &#9474;     warranties and prevails over any conflicting or additional terms      &#9618; 
 &#9474;     of any quote, order, acknowledgment, or other communication           &#9618; 
 &#9474;     between the parties relating to its subject matter during the term    &#9618; 
 &#9474;     of this Agreement.  No modification of this Agreement will be         &#9618; 
 &#9474;     binding, unless in writing and signed by an authorized                &#9618; 
 &#9474;     representative of each party.  



"
this is the last part of that .but i can't go ahead.then i open a new termnal and type javac .but it gives same as before installing java.                                       &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; For inquiries please contact: Sun Microsystems, Inc., 4150 Network        &#9618; 
 &#9474; Circle, Santa Clara, California 95054, U.S.A.                             &#9618; 
 &#9474;                                                                           &#9646; 
 &#9474; DLJ v1.1                                                  27APR2006ANS
"

---

### Post by michy99 on 2009-07-04
You have to accept the license to install. Use the tab key to choose 'yes' or 'accept' or whatever it says and press enter.

---

