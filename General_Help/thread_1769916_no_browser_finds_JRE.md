---
title: "no browser finds JRE"
date: 2011-05-28
forum: General Help
---

### Post by matt_knelsen on 2011-05-28
hello ubuntu community,

i'm running ubuntu 10.10, and no browser can identify my java JRE. i've tried with firefox 4 and chromium 11.0.696.71. the thing is i'm not using the standard openJDK-JRE that comes with the OS. i had to exchange it for the sun-java version, since i work with processing and arduino. and since then, my browsers can't open any java applet on a html page. i mean, they accuse they have the java plugin installed, but firefox crashes every time i try to open a page that requires java plugin, and chrome simply does not show the applet: a white space is all there is.

i've searched in a bunch of forums and tried every solution i faced: uninstalled the standard openJRE-openJDK, corrected the symlink in the /usr/lib/mozilla/plugins, even deleted the jre1.6.0_24 and installed the newest version (jre1.6.0_25) in /usr/java, exchanging the symlink, but still no luck.

firefox accuses the following error in terminal:

```
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object

```

is anybody having a similar problem? i appreciate any help, thanks!

---

### Post by linuxinstalledfromhdd on 2011-05-28
It's a pretty common problem with Java.  Try using a walkthrough:

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

---

### Post by matt_knelsen on 2011-05-28
thanks for your answer, linuxinstalledfromhdd.

in the walkthrough, all i found was that i had to install sun JRE, which i already did. the last thing i tried was to manually install the jre1.6.0_25 version, and even thought i exchanged the symlink in usr/mozilla/plugins, firefox still crashes. chromium simply does not start the applets. to  me, seems like a bad defined path somewhere, but i don't know exactly where to look at.

---

### Post by lordadi on 2011-05-28
run
```
sudo update-alternatives --config java
```

This will get ubuntu to tell you which java installs it is aware of. What does it give you?

---

### Post by matt_knelsen on 2011-05-28
gives me the following:


```
There are 1 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                  Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-6-sun/jre/bin/java   63        auto mode
* 1            /usr/lib/jvm/java-6-sun/jre/bin/java   63        manual mode
```

have i messed up java by manually installing the latest JRE version? i tried to choose the auto mode, started up firefox, but still no luck: crashed when i tried to open the java test page.

---

### Post by lordadi on 2011-05-28
The problem is that your manually installed java is not available to the system, so when Firefox looks in the symlink directory - it doesn't find a java that the system knows exists.

Give me a minute while I dig up the update command.
----EDIT-----
This is not the way I did it, but this should work:

```

sudo add-apt-repository ppa:sun-java-community-team/sun-java6 
sudo apt-get update 
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-jdk
java -version

```

---

### Post by lordadi on 2011-05-28
Follow that up with
```
sudo apt-get install sun-java6-plugin
```
and that should take care of your plugin issues.

---

### Post by airspoon on 2011-05-28
Hi lordadi, I'd hate to hijack the thread, but I'd also hate to start a new thread on the same subject. Anyway, I just recently installed Sun Java JRE and JDK mannually on 11.04 through ```
 sudo apt-get install sun-java6-jdk sun-java6-jre
```.

I'm not noticing any problems yet and I have left the open-jdk and jre as the default for the time being (which is probably why I haven't noticed any problems). I'm kind of worried about breaking it, if I switch over to the Sun jre and jdk as the default.

Should I try to reinstall the Sun jre and jdk through the method you suggested in the post above this one? If so, should I just run that command or should I uninstall the Sun jre and jdk first with a: ```
sudo apt-get  --purge remove
```

Thanks.

---

### Post by lordadi on 2011-05-28
> **airspoon said:**
> Hi lordadi, I'd hate to hijack the thread, but I'd also hate to start a new thread on the same subject. Anyway, I just recently installed Sun Java JRE and JDK mannually on 11.04 through ```
 sudo apt-get install sun-java6-jdk sun-java6-jre
```.

Where did you get the sun versions from? As per [http://packages.ubuntu.com/natty/java/](http://packages.ubuntu.com/natty/java/) , Natty does not have sun versions available.

---

### Post by airspoon on 2011-05-28
I got them through "apt-get". They were there and are even showing up through 
```
sudo update-alternatives --config java
```

They aren't supposed to be in "apt-get"?

---

### Post by lordadi on 2011-05-28
Then it sounds like you have installed the sun versions. In this case, your only real cause for concern is that stuff may not work when the sun packages are made defaults.

Can you post ```
sudo update-alternatives --config java
```

---

### Post by airspoon on 2011-05-28
Sure.

```
There are 2 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                      Priority   Status
------------------------------------------------------------
* 0            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      auto mode
  1            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      manual mode
  2            /usr/lib/jvm/java-6-sun/jre/bin/java       63        manual mode

Press enter to keep the current choice
[*], or type selection number: 

```

Would it better if I uninstalled them and then reinstalled using the mthod described by you? I've heard of PPAs before but I'm not sure what they are or any benefits to them. Thanks.

---

### Post by lordadi on 2011-05-28
PPAs are Personal Package Archives - they are used to package and provide code that may not be provided in the main repositories. For this reason, they are also more of a security concern.

The major benefit to the use of PPAs is that you will be notified of updates, but as mentioned above, this is not necessarily always safe. Given that you already have the sun version (and it looks like it was properly packaged for Ubuntu), I don't see the point in changing one PPA (assuming some PPA is being used to provide the sun version) for another. :)

---

As you can see, both the default openJDK version and the sun versions are installed. Now, if you want to test to see whether your sun install works, you would run the command again and select 3. This would tell the system to look at the sun installation for any java necessities. From what I can tell, the only potential problem you may have is that Firefox may not have the java plugin installed to use the sun version.

If you're feeling brave, you can try it (you can always change back to 0 to undo the "damage").

---

### Post by airspoon on 2011-05-28
Thank you for clearing that up for me. Although I'm not particularly
 feeling brave, I'm going to have to test out the Sun java to see if it works, seeing how the flex sdk requires the Sun jdk (from my understanding). In worst case, I'll only have to change the default back to the open-jdk, right? 

Now I know how to change the default jre, but what about the jdk? Do I also have to change the default jdk and if so, how would I go about doing that?

Anyway, thanks again!

---

### Post by matt_knelsen on 2011-05-28
thanks lordadi, i got it working. i added the repository to the PPAs, removed the sun java installation, and reinstalled through apt-get. now it seems to work both in firefox and chromium.

thanks again!

---

### Post by lordadi on 2011-05-28
You're welcome Matt!

Airspoon, you are right on the first count.

For changing the JDK, I think that the JDK is tied (in a sense) to the base JRE running on the system (logically, makes no sense to run an applet with 6.24 when it was compiled with 6.25 and features may have been superseded). My guess is that the sun JDK will also become the default. I think 

```
javac --version
``` will show you what's underneath. If not, post a new thread, a SOLVED one is not likely to get too much more attention from more knowledgeable folks :)

---

### Post by lordadi on 2011-05-28
Actually, I was wrong airspoon. You can change your javac version the same way you change the JRE:

```
sudo update-alternatives --config javac
```

You can substitute almost any java compiler etc for "javac" - just be careful what you change so that you can change it back when needed :D

---

### Post by dsat on 2011-06-06
Maybe someone have still problems with sun-java6:

I had problems with sun-java6 with the retro game page nintendo8.com, which was posted on 
  [http://ubuntuforums.org/showthread.php?p=2608945](http://ubuntuforums.org/showthread.php?p=2608945)

Now it works with
  java-6-openjdk
on ubuntu 11.04 for me. 

I used the openjdk-6* packages, and for functionality in firefox you have to use the package icedtea-plugin!

---

### Post by lordadi on 2011-06-07
That's right dsat, if you use:

[LIST=1]
[*]openJDK, you MUST use icedtea plugins.
[*]SUN java6, you MUST use the sun-java6-plugins.
[/LIST]

---

### Post by aminorex on 2011-08-13
I have sun-java6-jre and sun-java6-plugin installed from the ppa, but chromium has started giving me "The java plug-in has been blocked because it is out of date", and when I try the "Run  this time" button, the applet always fails to run/load.  Any clues?

---

### Post by MarkieB on 2012-03-14
no longer participating in ubuntuforums.org

---

