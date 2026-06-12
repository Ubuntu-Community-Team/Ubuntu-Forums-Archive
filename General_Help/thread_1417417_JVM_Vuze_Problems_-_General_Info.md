---
title: "JVM Vuze Problems - General Info"
date: 2010-02-27
forum: General Help
---

### Post by diesel59 on 2010-02-27
Hi There,

I am relativity new to Linux so your patience would be greatly appreciated. Yesterday I had to set up eclipse and was playing around with my JVM settings.  Unfortunately now I have jumbled things around with my JVM's and was wondering if I could get some assistance to straighten things out? So here is what I did.

1. I removed my open jdk installation
$ sudo apt-get remove openjdk-6-jre openjdk-6-jre-headless icedtea-6-jre-cacao icedtea6-plugin default-jre default-jre-headless icedtea-gcjwebplugin

2. Ran a command to set my alternatives (I was playing around so I do not know which one was applied)

$ sudo update-alternatives --install "/usr/bin/java" "java" "/usr/local/jdk1.6.0_18/jre/bin/java" 1

$ sudo update-alternatives --set java /usr/local/jdk1.6.0_18/jre/bin/java

**So now I have the following settings**

which java **returns** /usr/bin/java

In my /etc/alternatives folder I have two links with the following targets

java** has a target** /usr/lib/jvm/java-6-openjdk/jre/bin/java

java_vm **has a target** /usr/lib/jvm/java-6-sun/jre/bin/java_vm

And in my /usr/lib/jvm folder I have the following JVM's

me@/usr/lib/jvm$ ls -a
.   default-java        java-1.6.0-openjdk  .java-6-openjdk.jinfo  java-6-sun-1.6.0.16
..  java-1.5.0-gcj-4.4  java-6-openjdk      java-6-sun             .java-6-sun.jinfo

Ok so it's pretty messy.  But now everything seems to run ok on my PC except for Vuze which returns

$ azureus %f
exec: 19: /usr/local/jdk1.6.0_18/bin/java/bin/java: not found


when I try to run it.

my /usr/bin/azureus looks like

#!/bin/sh

# Include java-wrappers
. /usr/lib/java-wrappers/java-wrappers.sh

JAVA_CLASSPATH="/usr/lib/jni:/usr/lib/java"
VUZE_BIN="/usr/bin/vuze"

find_java_runtime openjdk sunmin5

find_jars Azureus2 log4j-1.2 commons-cli swt

if [ ! -x $VUZE_BIN ]; then
    UI=-Dforce.ui=az2
fi

run_java -Dazureus.install.path="$HOME/.azureus" $UI \
    -XX:CompileCommand=exclude,com/aelitis/net/udp/uc/impl/PRUDPPacketHandlerImpl\$5,runSupport \
    org.gudy.azureus2.ui.common.Main "$@"



and my JAVA_HOME and PATH is

JAVA_HOME=/usr/local/jdk1.6.0_18/bin/java

PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/jdk1.6.0_18/bin:/usr/java/jdk1.6.0_18:/usr/local/jdk1.6.0_18/bin

This JDK does exist at the location

me@me:/usr/local$ ls -a
.  ..  bin  etc  games  include  jboss-seam-2.2.0.GA  jdk1.6.0_18  lib  man  netbeans-6.7.1  sbin  seam  share  sr


I suppose my question is why is vuze looking for this link and where is this target coming from? Also how do I clean up all of the JVM's I am not using?

Any help would be greatly appreciated and apologies if I have placed this in the wrong location

---

### Post by mobrien118 on 2013-03-25
I know this is an old thread, but I'm stuck in the same place.

I removed openjdk because it was causing some problems with Azureus/Vuze (I suspect), and now it won't load at all. Exactly the same as your thread.

I'm going through the code to see if I can solve this, but was hoping maybe I could fast track solving it by bumping this thread.

If I solve this before I hear back, I'll post the solution.

Thanks!

---

### Post by oldos2er on 2013-03-25
[COLOR=#000000]If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.[/COLOR]

---

