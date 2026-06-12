---
title: "where can I find java6-sdk .. not jre ?"
date: 2012-04-24
forum: General Help
---

### Post by dragonfly41 on 2012-04-24
I'm trying to install a non Ubuntu deb package .. but I get this message

> Dependency is not satisfiable: java6-sdk


Three Java alternatives installed are shown by running this command

sudo update-alternatives --config java

  Selection    Path                                                               Priority   Status
------------------------------------------------------------
   0            /usr/lib/jvm/java-6-openjdk/jre/bin/java          1061      auto mode
   1            /usr/lib/jvm/java-6-openjdk/jre/bin/java          1061      manual mode
* 2            /usr/lib/jvm/java-6-sun/32/jre1.6.0_31/bin/java   1         manual mode
   3            /usr/lib/jvm/jdk1.7.0/jre/bin/java                           2         manual mode


The current selection (2) is ..

java version "1.6.0_31"
Java(TM) SE Runtime Environment (build 1.6.0_31-b04)
Java HotSpot(TM) Server VM (build 20.6-b01, mixed mode)

but where can I get java6-sdk to be installed as another alternative?

---

### Post by techsupport on 2012-04-24
hi there Dragonfly.. What is the name of the program you are trying to install? What version of Ubuntu are you running?

thank you.



> **dragonfly41 said:**
> I'm trying to install a non Ubuntu deb package .. but I get this message




Three Java alternatives installed are shown by running this command

sudo update-alternatives --config java

  Selection    Path                                                               Priority   Status
------------------------------------------------------------
   0            /usr/lib/jvm/java-6-openjdk/jre/bin/java          1061      auto mode
   1            /usr/lib/jvm/java-6-openjdk/jre/bin/java          1061      manual mode
* 2            /usr/lib/jvm/java-6-sun/32/jre1.6.0_31/bin/java   1         manual mode
   3            /usr/lib/jvm/jdk1.7.0/jre/bin/java                           2         manual mode


The current selection (2) is ..

java version "1.6.0_31"
Java(TM) SE Runtime Environment (build 1.6.0_31-b04)
Java HotSpot(TM) Server VM (build 20.6-b01, mixed mode)

but where can I get java6-sdk to be installed as another alternative?

---

### Post by nimzter on 2012-04-24
What platform are you using ? Netbeans, Ecplipse ?

---

### Post by dragonfly41 on 2012-04-24
Platform: ubuntu 10.10 32 bit

Package:  resin_4.0.27-i386.deb (open source)

from here ...

[http://www.caucho.com/download/](http://www.caucho.com/download/)

Thanks.

---

### Post by techsupport on 2012-04-24
> **dragonfly41 said:**
> Platform: ubuntu 10.10 32 bit

Package:  resin_4.0.27-i386.deb

from here ...

[http://www.caucho.com/download/](http://www.caucho.com/download/)

Thanks.

Are you running a 64 bit version of Ubuntu? Is it a "forced" install of that 32-bit package? Maybe if you were running a 32-bit version of Ubuntu and installing a 32-bit version of Sun Java (not OpenJDK)  they would get along better - imho.  Just a shot in the dark here. I doubt this is really anything to do with Java. Maybe you need to use a particular version of the original Sun Java and not the open source Java that is found in the ubuntu repositories.  Does that sound like that might apply to what you are experiencing?   That software has a forum of it's own, and I would probably post a question there as well. (for right now?) What are the requirements that they say you need to have?

---

### Post by QIII on 2012-04-24
We've gotten a bit off the mark here, folks.  It doesn't matter what program the OP is installing, it's not a matter of OpenJDK vs Java JRE, what development IDE the OP is planning on using or even whether something is "forced".  32 vs 64 bit does matter.

The answer is to go to [http://www.oracle.com/technetwork/java/javaee/downloads/index.html](http://www.oracle.com/technetwork/java/javaee/downloads/index.html), download the Java EE 6 SDK and install it per the instructions.

Java is no longer in the Ubuntu repos because Oracle decided to take their ball and go home.  Nobody is licensed to have it in their repos any longer.

---

### Post by techsupport on 2012-04-24
> **QIII said:**
> We've gotten a bit off the mark here, folks.  It doesn't matter what program the OP is installing, it's not a matter of OpenJDK vs Java JRE, what development IDE the OP is planning on using or even whether something is "forced".

The answer is to go to [http://www.oracle.com/technetwork/java/javaee/downloads/index.html](http://www.oracle.com/technetwork/java/javaee/downloads/index.html), download the Java EE 6 SDK and install it per the instructions.

Java is no longer in the Ubuntu repos because Oracle decided to take their ball and go home.  Nobody is licensed to have it in their repos any longer.

I write scripts to install software for Sun Java, and I know what I am talking about when I say that "perhaps" they should find out what the requirements are for the software they want to run might be.  Sometimes the developers use a particular version of Java. And only that version of Java will work with their program.  That's the mark I was aimming for with what I said. Hopefully the developer forum for that software can let them know what version of Java they need to be running that is proven/shown to work with that program they wrote. :)  Maybe the web site has some specifications listed about which Java they need to have installed. We can only guess at what that might be for now.

---

### Post by QIII on 2012-04-24
Not to be offensive (so don't take offense), I *DEVELOP* in Java.  I'm pretty sure I am aware of what is  necessary.  He needs Java 6 EE SDK.  Since Java 7 is only 9 months old and just recently hit Update 2, what is out there that requires it is very new or only still in development.

(I just checked.  What he is talking about is EE 6 certified.) 
    
   The OP could also download and install one of the bundles and get the JDK as well.

The SDK is downloaded and installed from Oracle's website.

---

### Post by techsupport on 2012-04-24
> **QIII said:**
> Not to be offensive (so don't take offense), I *DEVELOPE* in Java.  I'm pretty sure I am aware of what is  necessary.  He needs Java 6 EE SDK.  Since Java 7 is only 9 months old and just recently hit Update 2, what is out there that requires it is very new or only still in development.

(I just checked.  What he is talking about is EE 6 certified.) 
    
   The OP could also download and install one of the bundles and get the JDK as well.

The SDK is downloaded and installed from Oracle's website.

That's true. But if I was having this problem I would still post the question in the appropriate software forum where the developers would know first-hand what specifications they must be running on their system first. Only they would know. Right? I would still like to know if she is running a 64 bit system of Ubuntu with 64 bit Java and using a 32-bit program. That could be important.

---

### Post by QIII on 2012-04-24
And I said that 32 vs 64 bit was important

It's a Java EE 6 certified application server.  Says so right on the website.

---

### Post by techsupport on 2012-04-24
> **QIII said:**
> And I said that 32 vs 64 but was important

It's a Java EE 6 certified application server.  Says so right on the website.

Just to be clear.. The software package they are installing from that web site is a 32-bit debian installation package. Maybe they are force installing it on a 64-bit version of Ubuntu? Unless they have multiarch enabled already, that could be related to whatever they are experiencing. Ask the software developers in their forum what they suggest next. They can give you a definitive thumbs up on running it in Ubuntu 64-bit. That is what I would suggest for now. Over and out.

---

### Post by QIII on 2012-04-24
"Platform: ubuntu 10.10 32 bit"

Not trying to be a butt (24 years in the Army made it so I don't have to "try"), but he seems to have a simple dependency problem.  Nothing more earth shattering than that.

---

### Post by techsupport on 2012-04-24
> **QIII said:**
> "Platform: ubuntu 10.10 32 bit"

Did they create the package to run on Ubuntu 10.10 32 bit? Maybe they need to run it on 11.10? Maybe it was made for 9.04? I don't know.  What do the guys over in the developer forum have to say? They have to know. :)

Cheers

---

### Post by QIII on 2012-04-24
> **techsupport said:**
> Did they create the package to run on Ubuntu 10.10 32 bit? Maybe they need to run it on 11.10? Maybe it was made for 9.04? I don't know.  What do the guys over in the developer forum have to say? They have to know. :)

Cheers

Maybe a lot of things.

First and easiest thing to do is to install the unfulfilled dependency and see if that rectifies the problem.  As a developer, that would be the very first thing I'd say to someone who approached me with a similar issue.

Go to the developers if that doesn't work.

Sorry about seeming the gruff old man.  I'm the sort that goes for the direct, pragmatic solution rather than pulling my hair out about "maybes".

Just tell me how to kill the enemy.

---

### Post by techsupport on 2012-04-24
> **QIII said:**
> Maybe a lot of things.

First and easiest thing to do is to install the unfulfilled dependency and see if that rectifies the problem.  As a developer, that would be the very first thing I'd say to someone who approached me with a similar issue.

Go to the developers if that doesn't work.

Sorry about seeming the gruff old man.  I'm the sort that goes for the direct, pragmatic solution rather than pulling my hair out about "maybes".

Just tell me how to kill the enemy.

Very accurate advice too. Whenever I try to install software that isn't specific about what kind of system it was designed to run on, I just ask the developers. They have to know. They can provide a work-around that will work too.  Everything is a maybe here at this point. Or you can ask these guys:

[http://www.ubuntu.com/business/services/overview](http://www.ubuntu.com/business/services/overview)

I know they can make it work one way or another. :) 

The original reason I asked what the name of the software was, is to figure out if this for a commercial enterprise production system. Sounds like it might be. The OP may need this Java software to not crash on them later on down the road too and avoid that kind of hassle. Ubuntu support may even be able to provide a custom made program to do the same thing already tested with the latest version of Ubuntu OS. 

Cheers.

---

### Post by dragonfly41 on 2012-04-25
Thanks for the pointers .. I had not expected such a long thread which now deserves a full reply.

Firstly to answer one question .. this was a question related to ubuntu 32 bit.   I am developing on a 32 bit computer.  So 32 bit vs. 64 bit discussion is not really relevant.

Now I was intrigued about where this java dependency check was applied to see if i could hack the deb package .. so I did some research and found this ..

[http://thedarkmaster.wordpress.com/2008/05/24/how-to-create-manipulate-a-deb-file-of-a-compiled-application/](http://thedarkmaster.wordpress.com/2008/05/24/how-to-create-manipulate-a-deb-file-of-a-compiled-application/)

and this ..

[http://ubuntuforums.org/showthread.php?t=636724](http://ubuntuforums.org/showthread.php?t=636724)

I applied the useful bash script (gedit version in #post 5) to the problem deb and this is the output of control ..

> Package: resin
Version: 4.0.27
Section: web
Priority: optional
Architecture: i386
Maintainer: Scott Ferguson <ferg@caucho.com>
Provides: resin
Description: Resin application server
Depends: java6-sdkI did try editing the line Depends: java6-sdk to Depends: java-6-openjdk .. but no joy.
 
...

Then I read this in caucho forum ..

[http://forum.caucho.com/showthread.php?t=28852](http://forum.caucho.com/showthread.php?t=28852)

> 
Java 6 EOL notification
Oracle has announced that Java 6 will go End of Life on the third quarter of 2012. Has Resin 4 been certified to run on Java 7?

When I last enquired the recommendation from Caucho was to stay on Java 6 at the time. We do not want to be running on EOL'd code with no way to get new patches.

I see the majority of people in the forum are still on Java 6, what do they think about migration to Java 7?

Reply from caucho:  
After 4.1 is released we plan on moving to java 7.

At that time we will switch the JDK we use to run our tests to Java 7.
I did post a question on "Dependency is not satisfiable: java6-sdk" as suggested 
but no reply received as yet.

...

I then remembered trying to install an earlier version of resin on ubuntu image on Amazon.

[http://forum.caucho.com/showthread.php?t=28407](http://forum.caucho.com/showthread.php?t=28407)

[http://forum.caucho.com/showthread.php?t=28410](http://forum.caucho.com/showthread.php?t=28410)

but at that date java-6-sun was available in ubuntu repo

...

this is a resin thread explaining the installation

[http://wiki.caucho.com/Resin_Installation](http://wiki.caucho.com/Resin_Installation)

> 
"Installing Resin using the .deb package on Ubuntu and Debian"

We provide a Debian packaged version of Resin that Debian and Ubuntu users can take advantage of. It performs all of the installation steps above for you and creates all the recommended server and content directories. Simply download from the [http://caucho.com/download](http://caucho.com/download) download page and install using dpkg.

Alternatively, you can add Caucho's Debian repository to your system's repositories to use automated update tools like Synaptic and apt-get. To do this, add the following line to your /etc/apt/sources.list

deb [http://caucho.com/download/debian/](http://caucho.com/download/debian/) unstable universe 
deb [http://caucho.com/download/debian/](http://caucho.com/download/debian/) unstable multiverse 

After adding this line, update your local repository cache by running:

sudo apt-get update
sudo apt-get install resin 

I'm still exploring and will update when I get resin running.

---

### Post by techsupport on 2012-04-25
> **dragonfly41 said:**
> 

but at that date java-6-sun was available in ubuntu repo


Then just add the older repo to your currently installed Ubuntu and install the older sun package.  Make sure to uninstall any other instances of Java first. Remove the older repo to avoid broken pipes when you are done installing java-6-sun. I've had to use work-arounds like that before, and usually do the trick.

---

