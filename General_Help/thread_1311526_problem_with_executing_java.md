---
title: "problem with executing java"
date: 2009-11-02
forum: General Help
---

### Post by johnyjj2 on 2009-11-02
Hello :-)!

I've got problem with executing HelloWorld.jar which is part of CMU Sphinx (Sphinx4). I've got Ubuntu 9.10 and I installed JDK 6 Update 16 with NetBeans 6.7.1 from [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp).

Can anybody help me, please?

I try to execute it with the following:

```
mainacc@mainacc-laptop:~/tutorial/sphinx4-1.0beta3-bin/sphinx4-1.0beta3$ java -mx256m -jar bin/HelloWorld.jar
Exception in thread "main" java.lang.NoClassDefFoundError: javax/speech/recognition/GrammarException
```

And I tried to solve this problem by applying this ([http://freetts.sourceforge.net/docs/jsapi_setup.html](http://freetts.sourceforge.net/docs/jsapi_setup.html)), however it didn't help:

```
* Go to the lib directory.
* Type chmod +x ./jsapi.sh.
* Type sh ./jsapi.sh and view the BCL.
* If the BCL is acceptable, accept it by typing "y". The jsapi.jar file will be unpacked and deposited into the lib directory.
```

After installing Ubuntu, I installed (as explained earlier) JDK 6 Update 16 with NetBeans 6.7.1 but also I did the following:

```
myacc@myacc-laptop:~$ echo "export PATH=\$PATH:/usr/local/jdk1.6.0_16/bin" >> ~/.bashrc
myacc@myacc-laptop:~$ . ~/.bashrc
```

Thanks for help in advance :-)!
Greetings :-)!

---

### Post by dcstar on 2009-11-02
> **johnyjj2 said:**
> 
..........
And I tried to solve this problem by applying this ([http://freetts.sourceforge.net/docs/jsapi_setup.html](http://freetts.sourceforge.net/docs/jsapi_setup.html)), however it didn't help:

```
* Go to the lib directory.
* Type chmod +x ./jsapi.sh.
* Type sh ./jsapi.sh and view the BCL.
* If the BCL is acceptable, accept it by typing "y". The jsapi.jar file will be unpacked and deposited into the lib directory.
```
..........

So you did **exactly** as those instructions said?

---

### Post by johnyjj2 on 2009-11-03
Thanks for your help :-)!
Hm, rather yes. (At this moment I'm not at home so I cannot check it). I entered the lib directory, I changed privilidges, checked it by ls -l and it was correctly changed. Later, after executing sh ./jsapi.sh I saw the licence and agreed by pressing 'y'. However it showed some kind of problem and the file wasn't unpacked.
Greetings :-)!

---

### Post by Shredderwoods on 2011-01-31
> **johnyjj2 said:**
> Thanks for your help :-)!
Hm, rather yes. (At this moment I'm not at home so I cannot check it). I entered the lib directory, I changed privilidges, checked it by ls -l and it was correctly changed. Later, after executing sh ./jsapi.sh I saw the licence and agreed by pressing 'y'. However it showed some kind of problem and the file wasn't unpacked.
Greetings :-)!
Its quite late, but still.. can someone help me here:
this is the result that I get:
------------------------------
Accept (y/n)?: 
y
x - creating lock directory
x - extracting jsapi.jar (binary)
./jsapi.sh: 1428: uudecode: not found
restore of jsapi.jar failed
jsapi.jar: MD5 check failed
-------------------------------------

---

### Post by leopardb on 2011-01-31
> **Shredderwoods said:**
> Its quite late, but still.. can someone help me here:
this is the result that I get:
------------------------------
Accept (y/n)?: 
y
x - creating lock directory
x - extracting jsapi.jar (binary)
./jsapi.sh: 1428: uudecode: not found
restore of jsapi.jar failed
jsapi.jar: MD5 check failed
-------------------------------------

seems to me the line **./jsapi.sh: 1428: uudecode: not found** means that you don't have the uudecode program on your machine.

When that happens, you can look there : [U][http://packages.ubuntu.com](http://packages.ubuntu.com)

[/U]Then, in "Search the contents of packages" type "uudecode". You'll get the following result :
File     Packages
/usr/bin/uudecode     sharutils

So what you seem to need is in the package "sharutils".

sudo aptitude install sharutils

After that, uudecode should be known to your system (assuming /usr/bin is in you path, but it should) and you can try again the last steps.

Hope it helps.

---

### Post by Shredderwoods on 2011-02-09
> **leopardb said:**
> seems to me the line **./jsapi.sh: 1428: uudecode: not found** means that you don't have the uudecode program on your machine.

When that happens, you can look there : [U][http://packages.ubuntu.com](http://packages.ubuntu.com)

[/U]Then, in "Search the contents of packages" type "uudecode". You'll get the following result :
File     Packages
/usr/bin/uudecode     sharutils

So what you seem to need is in the package "sharutils".

sudo aptitude install sharutils

After that, uudecode should be known to your system (assuming /usr/bin is in you path, but it should) and you can try again the last steps.

Hope it helps.

Thanks man :p

---

