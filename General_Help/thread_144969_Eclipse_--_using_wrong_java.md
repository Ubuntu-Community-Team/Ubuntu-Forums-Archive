---
title: "Eclipse -- using wrong java"
date: 2006-03-15
forum: General Help
---

### Post by JustRandomName on 2006-03-15
Hi,

I have installed eclipse using:

```
sudo apt-get install eclipse-jdt
```

Everything went fine but when I launch eclipse the JVM that i uses is the gcj one, located at:

/usr/lib/jvm/java-gcj

I would like to tell eclipse to use the Sun version. I tried reconfiguring like so:

```

sudo update-alternatives --config java

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
 +    2        /usr/lib/jvm/java-gcj/bin/java
*     3        /usr/lib/j2re1.5-sun/bin/java

```

I selected option 3, tried eclipse again still the same problem.

I then tried using the -vm option for eclipse but it said that it was not a valid executable:

```
$ eclipse -vm /usr/lib/j2re1.5/sun/bin/java
```

What should I do?

Eclipse launches and works under the gcj, but the gcj fails to compile most of my code.

Thanks for your time

---

### Post by JustRandomName on 2006-03-15
Ummm....

This is like the 3rd time I have answered my own questions on this forum, but the solution is like follows:

Start eclipse and then go to "Window -> Preferences" click on Java and then Installed JVM and add the Sun JVM.

Sorry for wasting your time (again)! But as someone once said, I am not wasting time, I am making it easier for the next person to find ;)

---

### Post by testube_babies on 2006-04-09
this helped me, so it obviously wasn't a waste of time!  thanks!

---

### Post by dpm on 2006-04-11
Hi, 

I have the same problem, but the solution does not seem to work for me.

I have Sun's j2re1.5 installed and I'd like eclipse to use it instead of java-gcj, which is painfully slow on my system.

I first tried reconfiguring the java binary as you said, but in my case it was already set to the j2re, as I can also check from the command line:

```
$ java -version
java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)
``` 
Then I tried to specify the java runtime eclipse should be using from within the GUI (Window>Preferences>Installed JREs). There I specified **/usr/lib/j2re1.5-sun **as the JRE's home directory, gave a name to the new JRE and activated it (which effectively unclicks the original java-gcj runtime environment which was there by default).

Unfortunately, that did not work. Eclipse still seems to be using the java-gcj binary every time it is started. I also tried to use the -vm option when executing eclipse, but I got the same error you described (invalid executable). 

The main problem is that when invoked without options (as in /usr/bin/eclipse), eclipse seems to specify the java-gcj per default. On my system that's how eclipse is invoked:

```
/bin/bash /usr/bin/eclipse
/usr/lib/eclipse/eclipse -vm /usr/lib/jvm/java-gcj/bin/java -install /usr/lib/eclipse  -vmargs -Djava.library.path=/usr/lib/jni -Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.0/classmap.db -Dosgi.locking=none
``` 
I could not find anything on the forums mentioning this, but I'll keep looking.

Basically, all other applications that use java on my system seem to run fine, but eclipse is so slow I just can't work with it (note: my computer is fairly new, it is not that I'm trying to run this on old hardware).

Any help/comments will be greatly appreciated,

Thanks.

---

### Post by dpm on 2006-04-11
Well... 

Talking about answering one's own posts...

I just found the solution to my problem in the forums. My eclipse is now using suns's JRE and it is a lot faster! Now I can at least work with it.

I just had to edit the 

```
/etc/eclipse/java_home
``` 
file, which tells eclipse the order in which it should search for a JRE. The only thing I did then, was to put

```
/usr/lib/j2sdk1.5-sun
``` 
on top of the list. Ok, eclipse, as usual, is not overly fast (or at least not faster than in windows), but as I said, at least I can work with it.

Thanks.

---

### Post by jessecollins on 2007-04-23
desp,

Major thanks for your last post.  Solved my problem.  

Jesse

---

