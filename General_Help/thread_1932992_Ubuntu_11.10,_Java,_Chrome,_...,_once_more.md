---
title: "Ubuntu 11.10, Java, Chrome, ..., once more"
date: 2012-02-28
forum: General Help
---

### Post by LKeen on 2012-02-28
Hi everyone. I am now, after around 5 hours of google'ing, installing, removing, re-installing, google'ing again, …, at a point of which i think it's ok the start a thread, even with this maybe often asked question.

Thing is: I can't get Oracle Java working on my Ubuntu 11.10
Neither java itself, nor the plugin for google chrome although

java -version tells me:

java version "1.7.0_03"
Java(TM) SE Runtime Environment (build 1.7.0_03-b04)
Java HotSpot(TM) Server VM (build 22.1-b02, mixed mode)

I had OpenJDK installed and it did work at least. (I could start a java application on my local machine and it ran, though with very poor performance what led me to switch to Oracle Java)

Now, after following several guides i found via google i am as far as this:

The Java JDK is installed at:

/opt/java/32/jdk1.7.0_03

It includes the jre which is at:

/opt/java/32/jdk1.7.0_03/jre

(I took the 32 bit version since i found two recommendations for this ahead of the 64 bit version)

my /etc/profile looks like this:

…
JAVA_HOME=/opt/java/32/jdk1.7.0_03
PATH=$PATH:$HOME/bin:$JAVA_HOME/bin
JAVA_HOME=/opt/java/32/jdk1.7.0_03/jre
PATH=$PATH:$HOME/bin:$JAVA_HOME/bin
export JAVA_HOME
export JAVA_BIN
export PATH


google chrome is installed at:

/opt/google/chrome

there IS a plugins folder which contains a symbolic link to:

/opt/java/32/jdk1.7.0_03/jre/lib/i386/libnpjp2.so

also, in

 ~/.mozilla/plugins

there is a link to the libnpjp2.so since i have red that this is the way to go for google chrome too

further i also did:

sudo update-alternatives --install "/usr/bin/java" "java" "/opt/java/32/jdk1.7.0_03/jre/bin/java" 1

as well as:

sudo update-alternatives --set java /opt/java/32/jdk1.7.0_03/jre/bin/java


I now should be finished according to the guides.
As mentioned before

java -version gets me:

java version "1.7.0_03"
Java(TM) SE Runtime Environment (build 1.7.0_03-b04)
Java HotSpot(TM) Server VM (build 22.1-b02, mixed mode)


But now i try to start an application.
It's in 

~/Downloads/CreepTD and called CreepTD

i do 

java CreepTD 

and get the message that the mainclass was not found …
(it DID work when OpenJDK was installed)
Same problem when i try to start via filebrowser and ubuntu asks me whether to open or the execute it. Quick Terminal pop but then nothing happens.

Regarding chrome, there is no active java plugin when i check it via one of the installation verification sites, further, 

chrome://plugins does not list the java plugin.

I tried to start chrome via the terminal using

google-chrome –enable-plugins

but it ends up with the same story...


I am now just done and got no idea what else i could do.
help is very appreciated.
Can it be this rocketscience to install java on linux?

regards

---

### Post by idoitprone on 2012-02-28
> **LKeen said:**
> Hi everyone. I am now, after around 5 hours of google'ing, installing, removing, re-installing, google'ing again, &#8230;, at a point of which i think it's ok the start a thread, even with this maybe often asked question.

Thing is: I can't get Oracle Java working on my Ubuntu 11.10
Neither java itself, nor the plugin for google chrome although

java -version tells me:

java version "1.7.0_03"
Java(TM) SE Runtime Environment (build 1.7.0_03-b04)
Java HotSpot(TM) Server VM (build 22.1-b02, mixed mode)

I had OpenJDK installed and it did work at least. (I could start a java application on my local machine and it ran, though with very poor performance what led me to switch to Oracle Java)

Now, after following several guides i found via google i am as far as this:

The Java JDK is installed at:

/opt/java/32/jdk1.7.0_03

It includes the jre which is at:

/opt/java/32/jdk1.7.0_03/jre

(I took the 32 bit version since i found two recommendations for this ahead of the 64 bit version)

my /etc/profile looks like this:

&#8230;
JAVA_HOME=/opt/java/32/jdk1.7.0_03
PATH=$PATH:$HOME/bin:$JAVA_HOME/bin
JAVA_HOME=/opt/java/32/jdk1.7.0_03/jre
PATH=$PATH:$HOME/bin:$JAVA_HOME/bin
export JAVA_HOME
export JAVA_BIN
export PATH


google chrome is installed at:

/opt/google/chrome

there IS a plugins folder which contains a symbolic link to:

/opt/java/32/jdk1.7.0_03/jre/lib/i386/libnpjp2.so

also, in

 ~/.mozilla/plugins

there is a link to the libnpjp2.so since i have red that this is the way to go for google chrome too

further i also did:

sudo update-alternatives --install "/usr/bin/java" "java" "/opt/java/32/jdk1.7.0_03/jre/bin/java" 1

as well as:

sudo update-alternatives --set java /opt/java/32/jdk1.7.0_03/jre/bin/java


I now should be finished according to the guides.
As mentioned before

java -version gets me:

java version "1.7.0_03"
Java(TM) SE Runtime Environment (build 1.7.0_03-b04)
Java HotSpot(TM) Server VM (build 22.1-b02, mixed mode)


But now i try to start an application.
It's in 

~/Downloads/CreepTD and called CreepTD

i do 

java CreepTD 

and get the message that the mainclass was not found &#8230;
(it DID work when OpenJDK was installed)
Same problem when i try to start via filebrowser and ubuntu asks me whether to open or the execute it. Quick Terminal pop but then nothing happens.

Regarding chrome, there is no active java plugin when i check it via one of the installation verification sites, further, 

chrome://plugins does not list the java plugin.

I tried to start chrome via the terminal using

google-chrome &#8211;enable-plugins

but it ends up with the same story...


I am now just done and got no idea what else i could do.
help is very appreciated.
Can it be this rocketscience to install java on linux?

regards
One more thing? Is your os 64 bit and chrome is also 64 bit?
If yes to both then you have to reinstall java but have an 64 bit version
The command below will not fix your problem
```
sudo ln -s  /opt/java/32/jdk1.7.0_03/jre/lib/i386/libnpjp2.so /usr/lib/mozilla/plugins
```Your openjdk does not work because you did not install the icedtea plugin

Assuing that your java plugin dir path is correct and i hve the correct mozilla plugin path. Run this code and close and restart your browser

Oracle is the ones who made this difficult 
[http://www.youtube.com/watch?v=zqUQK8M4_ds](http://www.youtube.com/watch?v=zqUQK8M4_ds)
[http://www.osnews.com/comments/25441](http://www.osnews.com/comments/25441)
They revoke caniconcal distrubuters license

[http://technonstop.com/install-java-plugin-ubuntu-linux](http://technonstop.com/install-java-plugin-ubuntu-linux)

---

### Post by LKeen on 2012-02-28
OS is 64 bit and chrome is 64 bit but java is 32 bit.
( took 32 bit java because of reported problems with 64 bit java in general and with webstart applets in specific )

I don't want to use OpenJDK and/or IceadTea plugin. I removed both after i encountered the bad performance. Thats the reason why i want to switch to oracle Java. 

However, im going to give it another try with 64 bit java installation
(would Ubuntu 64 + chrome 32 + java 32 do the trick also?)

---

### Post by QIII on 2012-02-28
You would probably be just fine with 64 bit across the board.

I have been using and developing with the 64 bit JRE and JDK for a long time and have encountered no problems.

The pre-release Java 7 had it's expected bumps and pot holes.

---

