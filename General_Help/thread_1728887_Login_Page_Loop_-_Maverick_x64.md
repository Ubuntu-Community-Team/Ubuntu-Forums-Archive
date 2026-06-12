---
title: "Login Page Loop - Maverick x64"
date: 2011-04-14
forum: General Help
---

### Post by FlacAddict on 2011-04-14
Hi!

I've read other threads regarding this problem, but for some reason none of their solutions worked for me, so I'm posting my problem here as specific as I can. 

I'm an Ubuntu beginner but I'll do my best to provide the information needed.

I'm using an Ubuntu 10.10 Maverick Meerkat in a 64 bit system, dual boot with Windows 7 Ultimate x64.

--What happened before the problem--
1. I was installing tomcat together with jenkins and a sonar plugin. Everything worked fine for a duration of 4 hours. I had set a path environment variable (as was described in a tutorial which I was reading) for JDK, Groovy, Grails, and 2 aliases for starting and stopping Tomcat service in */etc/bash.bashrc*
2. I happened to play the wii/gamecube emulator Dolphin during the last 15 minutes of this 4 hour duration. As a result, after closing the window, my Ubuntu desktop environment became sluggish and slow after eating up memory. So I decided to do a restart.


--The problem--
For the first time in a while, the login page surprisingly popped up after the restart (I have my settings configured to login automatically to my account). After filling in the password and hitting enter, the login box disappears, then the screen goes black (then shows the ubuntu loading screen quickly). Then the login page shows itself again. I've tried logging in through safe mode but still nothing.

--The errors--
I tried using CTRL+ALT+F1 to open the console and I was able to login using my account. But an error is shown once I'm logged in the console. The errors apparently point towards how /bin or how /usr/bin is not included in the PATH environment variable (thus rendering most commands unusable like cd, ls, sudo, etc).

Here's another error log from .xsession-errors in /home/user I was able to open by using the Ubuntu LiveCD to access my filesystem.

> /etc/gdm/Xsession: Beginning session setup...
/etc/profile: 26: id: not found
[: 26: Illegal number: 
/etc/gdm/Xsession: 176: ls: not found
/etc/gdm/Xsession: ssh-agent not found!
/etc/gdm/Xsession: Setup done, will execute: gnome-session -f
exec: 1: gnome-session: not foundI've tried doing: *export PATH=/home/user/bin:/bin* or* export PATH=/home/user/bin:/usr/bin* in order to use the commands which were missing, but none of these helped.

Please, if anyone can pinpoint me to the right solution :(

Thank you in advance.

EDIT: I find doing: source ~/.profile reproduces the same errors when logging in the console, where /bin or /usr/bin is not included in the PATH environment variable. Any ideas? :(

---

### Post by FlacAddict on 2011-04-14
Fixed it. I won't recommend this fix generally because it's REALLY SPECIFIC TO MY PROBLEM. Unless you also did the same thing as me.

Anyway, the problem was caused by the PATH variable in /etc/environment.

Apparently following tutorials (taking the easy way out always) does have its consequences.

I added the Java paths like:

> JAVA_HOME="usr/lib/jvm/java-6-sun-1.6.0.24"
JRE_HOME="usr/lib/jvm/java-6-sun-1.6.0.24/jre"
PATH="...(other path):$JAVA_HOME:$JRE_HOME"

as was said in the tutorial. Apparently what the author meant by ...(other path) was the original PATH included in the /etc/environment which I disregarded. Thus overwriting the original PATH in the /etc/environment.

---

