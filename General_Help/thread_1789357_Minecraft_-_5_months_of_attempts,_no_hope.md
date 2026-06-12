---
title: "Minecraft - 5 months of attempts, no hope?"
date: 2011-06-23
forum: General Help
---

### Post by TheCadaver on 2011-06-23
So, I've been constantly been attempting to play minecraft, for the last 5 months or so; it has never worked without crashing. I contacted the experts, but they couldn't figure it out. Can't quite tell if it's a Java problem or an ATI+Ubuntu problem;

typing Java -version in terminal comes with:

java version "1.6.0_20"
OpenJDK Runtime Environment (IcedTea6 1.9.7) (6b20-1.9.7-0ubuntu1)
OpenJDK Server VM (build 19.0-b09, mixed mode)

I know that Minecraft will only support a Sun/Oracle jvm, as stated on their website, but every attempt to install this rather than openjdk results in either a catastrophic failure, or a so-called "outdated java". I uninstalled all versions of java, then did [FONT=Verdana]"sudo apt-get install sun-java6-jdk sun-java6-jre"[/FONT], then checked my java, and it said the above, that i have openjdk. However, when checking my applications, it appears that I have both.

The people at Mojang's irc have told me it was likely problem with ATI drivers and ubuntu, which is likely, as Minecraft still crashes when right-clicking Minecraft.jar and clicking "open with sun java 6 runtime" rather than opening it with openjdk. When running Minecraft from the terminal, I receive the following error:

```
Loading: net.java.games.input.LinuxEnvironmentPlugin
Failed to open device (/dev/input/event4): Failed to open device /dev/input/event4 (13)

Failed to open device (/dev/input/event3): Failed to open device /dev/input/event3 (13)

Failed to open device (/dev/input/event2): Failed to open device /dev/input/event2 (13)

Failed to open device (/dev/input/event1): Failed to open device /dev/input/event1 (13)

Failed to open device (/dev/input/event0): Failed to open device /dev/input/event0 (13)

Linux plugin claims to have found 0 controllers
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb7887424, pid=4429, tid=1735388016
#
# JRE version: 6.0_20-b20
# Java VM: OpenJDK Server VM (19.0-b09 mixed mode linux-x86 )
# Derivative: IcedTea6 1.9.7
# Distribution: Ubuntu 10.10, package 6b20-1.9.7-0ubuntu1
# Problematic frame:
# C  [+0x424]  __kernel_vsyscall+0x10
#
# An error report file with more information is saved as:
# /home/bruce/hs_err_pid4429.log
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   https://bugs.launchpad.net/ubuntu/+source/openjdk-6/
#
/usr/local/bin/minecraft: line 1:  4429 Aborted                 java -jar /home/bruce/.minecraft/minecraft.jar
```

At this point, i'll even take random suggestions... I've struggled enough with this.

---

### Post by dragonfly41 on 2011-06-23
Well here comes a random suggestion (untried) ...

install wine
install sun java 6 runtime through wine
run minecraft.jar in wine

does that work ???

---

### Post by TheCadaver on 2011-06-23
I've tried wine already, it gives the same result. in fact, I've never really liked wine for the fact that whenever there's a program i need to use, wine can't do it.

---

### Post by slooksterpsv on 2011-06-23
If 10.10 or lower, click Applications -> Accessories -> Terminal
If 11.04 or newer, click Dash -> type in Terminal -> Click on Terminal

Now in the terminal type in:

gksudo update-java-alternatives -s java-6-sun

Now restart your browser (or close the app if it's just the jar) and try to run again.

---

### Post by TheCadaver on 2011-06-23
that didn't do anything :|

---

### Post by TheCadaver on 2011-06-23
bump.

---

### Post by TheCadaver on 2011-06-23
...bump :|

---

### Post by slooksterpsv on 2011-06-23
Alrighty, run:

gksudo update-java-alternatives -l

And let's see what java's it says we have installed.

EDIT: Not to brag but just want to show it does work on Ubuntu with ATI.

I ran java -jar <minecraft file> and it works (for the paid version). Using Sun Java, not OpenJDK

For the free, I had to install: sun-java6-plugin (you have to enable partner repositories first before you'll find it). And then used the gksudo update-java-alternatives -s java-6-sun
Restarted my browser and the one online works too.

---

### Post by TheCadaver on 2011-06-23
It's not that it doesn't work with ubuntu + ati. it's just that mojang say there's been cases where that's the problem. also, neither of those worked. :|

---

### Post by slooksterpsv on 2011-06-24
When you run the above (or here I'll type it in again), what does it show/output? If you could copy and paste it here, that would help us a lot:

sudo update-java-alternatives -l

---

### Post by TheCadaver on 2011-06-24
java-6-openjdk 1061 /usr/lib/jvm/java-6-openjdk
java-6-sun 63 /usr/lib/jvm/java-6-sun

---

### Post by slooksterpsv on 2011-06-24
> **TheCadaver said:**
> java-6-openjdk 1061 /usr/lib/jvm/java-6-openjdk
java-6-sun 63 /usr/lib/jvm/java-6-sun

I would suggest removing openjdk if you don't need it.

sudo apt-get remove openjdk-6-jre

and make sure the java plugin is installed:

sudo apt-get install sun-java6-plugin

If after all that it doesn't work, I'm stumped.

---

### Post by TheCadaver on 2011-06-28
...nope. typing java -version still comes up with that result, even after autoremove, in which i removed around a quarter-gigabite of openjdk stuff. Should have been completely removed, gone. yet when i type in that command, i get "openjdk" as a reply. However, now minecraft's "launch with opejdk" is gone, and there is a "run with sun java runtime" option, however when using that, i get the same crash result. I really beleive it's not the java...

---

### Post by derklempner on 2011-06-28
Are you using a dual-monitor setup?

---

### Post by TheCadaver on 2011-06-29
nope.

---

### Post by dragonfly41 on 2011-06-30
Perhaps try installing [http://www.jedit.org](http://www.jedit.org) to launch your minecraft.jar?

You might be able to monitor what's going on.

---

### Post by arius13721 on 2011-06-30
I'm not at an Ubuntu box at the moment, but ensure that if you're running a 64-bit version of Ubuntu that you're also running the 64-bit version jre when you launch MC.

---

### Post by TheCadaver on 2011-07-01
/i found out it wasn't a java problem, but likely a problem between fglrx and ubuntu. just sold my graphics for an nvidia which i'll receive later this week.

---

### Post by slooksterpsv on 2011-07-01
> **TheCadaver said:**
> /i found out it wasn't a java problem, but likely a problem between fglrx and ubuntu. just sold my graphics for an nvidia which i'll receive later this week.

Like you said before, that's good. I apologize for trying to fix "java", I just know 90% of the apps I use don't work in OpenJDK they need Sun Java. So again I apologize. Did you even try the drivers from ATI and not the open source FGLRX ones?

---

### Post by TheCadaver on 2011-07-02
> **slooksterpsv said:**
> Like you said before, that's good. I apologize for trying to fix "java", I just know 90% of the apps I use don't work in OpenJDK they need Sun Java. So again I apologize. Did you even try the drivers from ATI and not the open source FGLRX ones?

No, it's okay. In fact, I'd much rather have sun java, so I'm going to continue this thread in getting me sun java.

Also, the drivers from ATI don't work as I recall

---

### Post by Phil Stone on 2011-08-31
> **TheCadaver said:**
> 
Also, the drivers from ATI don't work as I recall

the ATI drivers for their gfx cards on linux do not fulfill thier potential, unfortunately. for other games i play I can get really hype gfx on the windows box but not on the linux one pity) However minecraft is not GPU blackhole so potentially not an issue (well, until I want to dl hi-res texpacks heheh). 

I was experienecing some sun-java install issues. eventually,  I followed these instructions
[http://ubuntuforums.org/showthread.php?t=1508424&highlight=java+jvm](http://ubuntuforums.org/showthread.php?t=1508424&highlight=java+jvm)
 like a sheep and got sun-java-6 installed :) / :/ 
(you have to follow the link about update-ing the repository to include the partner repository where sun-java is. and its about half way down the page to update your apt-get and install the java 6)

so I downloaded the purchased game (linux version) from [http://www.minecraft.net](http://www.minecraft.net) 
I had to set the permissions so that it is executable as a program in properties. right clicked the package and browsed through to run with sun java 6

and omicron it works!!!  (so far - im in world that is. may crash yet but hope not) - so maybe try loading the ati drivers on - afraid thats a whole nother hassle but you can get them from 
the ati site

ffi minecraft search yogscasts - minecraft first night on youtube lol
here... [http://www.youtube.com/watch?v=4UdEFmxRmNE](http://www.youtube.com/watch?v=4UdEFmxRmNE)

now do excuse me I have maps and traps to craft - let alone networking my other *nix box and setting up a private minecraft server. see you in another 5 months.............

Woot!

really hope you get it going.
Phil

---

### Post by goldshirt9 on 2011-08-31
> **Phil Stone said:**
> 

now do excuse me I have maps and traps to craft - let alone networking my other *nix box and setting up a private minecraft server. see you in another 5 months.............

Woot!

really hope you get it going.
Phil
ha ha ha nice one

---

