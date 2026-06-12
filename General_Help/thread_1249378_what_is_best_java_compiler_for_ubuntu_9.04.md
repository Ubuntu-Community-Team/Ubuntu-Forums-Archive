---
title: "what is best java compiler for ubuntu 9.04?"
date: 2009-08-25
forum: General Help
---

### Post by Len Tyree on 2009-08-25
tried to compile a java program within ubuntu, got a message saying unable to compile, no javac compiler...
also got a message showing the possible java compilers available, as shown here...

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

copied in via apt-get, install, the sun-java5-jdk compiler.  but did not work; looks like it did but still can't compile.

so, which is the best java compiler to download for ubuntu, please, anybody?  

thanks for any help...len tyree.

---

### Post by Mighty_Joe on 2009-08-25
> **Len Tyree said:**
> 
copied in via apt-get, install, the sun-java5-jdk compiler.  but did not work; looks like it did but still can't compile.


Did you get the same error message?  If so, you may need to take one more step and tell Ubuntu [which java to use]("https://help.ubuntu.com/community/Java")
I'd go with the sun-java6-jdk package.  Newer is better, right?

---

### Post by Len Tyree on 2009-08-27
SOLVED

thanks mighty_joe...

did what you said, installed sun-kava6-jdk.  works fine now...

however, i must take exception to your statement, "newer is better" not always true; also "bigger is better"; also "latest is greatest", and a few other phases/axioms.  (but just joking), really appreciate the help.  

len tyreehttp://ubuntuforums.org/images/icons/icon7.gif

---

### Post by Bear Knuckle on 2009-08-27
The question Java5 or Java6 is a question of, do you need the new features in Java6?

---

### Post by Len Tyree on 2009-11-30
SOLVED - Thanks all.  Len.

---

