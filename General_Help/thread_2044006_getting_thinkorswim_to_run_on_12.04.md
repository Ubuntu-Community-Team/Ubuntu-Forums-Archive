---
title: "getting thinkorswim to run on 12.04"
date: 2012-08-17
forum: General Help
---

### Post by LLCoolJeff on 2012-08-17
I am trying to get thinkorswim, a stock options and futures tradeing platform to run on ubuntu and having some trouble. I have a support ticket with the company, but thought I would put something here as well in case there is an obvious solution...

Here is what is happening:

1. install goes good, after application opens, java uses up all of CPU sometimes greater than 100% in top (?).
2. applications runs like crap for a minute and then freezes, I eventually have to kill it using (sudo pkill -9 java)
3. after killing the application, if I try running it again, it never initializes. It only runs off of the end of the install when it automatically runs (I have tried unchecking run after install, and it never runs period after that.

So what could be stopping it from running after being installed? It gets stuck at an auto update window that looks like this:

[IMG]http://i47.tinypic.com/k9dnid.png[/IMG]

I have tried:

1. different version of java, even installing a completely different one (6 update 31) in a different directory and telling the program to use that version (as read here : [http://askubuntu.com/questions/127210/thinkorswim-crash-in-12-04](http://askubuntu.com/questions/127210/thinkorswim-crash-in-12-04) at the end)
2. I have tried installing thinkorswim in the home folder
3. Installing java in wine and then getting the windows version of thinkorswim, and it behaved the same way.

So my main question is dealing with the not running after it runs automatically after the install (picture above^^^^)

and the my secondary question would be why java maxes out CPU and then freezes the application...

I realize it will be hard to diagnose a third party app, but just seeing if anyone might have any input or possible problems..

---

### Post by OLFP on 2012-08-28
First, please contact TDAmeritrade and complain about their non-existent Linux support. Don't back down, they will claim they do not have any Linux customers. Let them know there are plenty of us trading on Linux, and if they want our business they need to fix their buggy software.

So far, I've had the best luck on Oracle's 32 bit Java 6u31. I couldn't get any 64bit java version to work. I might get some errors on start-up, but if I restart a few times, it'll eventually work correctly. 

You'll need to go to oracle's site to get it.  Install it somewhere separately, since thinkorswim will be the only program using it. I put it in /home/"user"/java.

Then edit the top of the thinkTDA script to point to the 6u31 version. It's wherever you installed TOS. 

Mine looks like this.
```

# Uncomment the following line to override the JVM search sequence
 INSTALL4J_JAVA_HOME_OVERRIDE=/home/floyd/java/jre1.6.0_31
# Uncomment the following line to add additional VM parameters
# INSTALL4J_ADD_VM_PARAMS=

```

If that doesn't work keep trying different versions of java. Just install them to the same directory and keep editing the version number on that thinkTDA script.

BTW, I have Windows7 laptop I use a a back-up. TOS is just as buggy on Windows. TDAmeritrade is ruining it all around.

If someone else uses another platform for day trading, please speak up. I'm so tired of the quality control at TDAmeritrade. TOS used to be stable, until they just kept piling "features" on.

[http://www.prodigiorts.com/](http://www.prodigiorts.com/) Looks promising, and they actually take interest in Linux issues.  I think they go live in September.

---

### Post by coldaspetr on 2012-08-28
Hi OP,

I was having a very similar issue, let me know if this resolves it for you. Basically I noticed it worked when it installed, guessing because it had sudo privileges. 

Here is how I wrote a little executable script to run the app and get past the update screen. 

First make sure a thinkorswim executable is on the desktop.

open terminal
[PHP]gedit runthinkorswim.sh[/PHP]

paste this
[PHP]#!/bin/bash
cd Desktop
gksudo thinkorswim[/PHP]

save, exit out of app.

in terminal
[PHP]chmod 0755 runthinkorswim.sh[/PHP]

now you have an executable script that launches thinkorswim after you enter the password. 
hope this helps.

---

### Post by troysos on 2012-08-29
I don't use thinkorswim but I do trade and use Ubuntu full time. It would be nice to see some apps for traders using Ubuntu.

---

### Post by coldaspetr on 2012-08-30
> **troysos said:**
> I don't use thinkorswim but I do trade and use Ubuntu full time. It would be nice to see some apps for traders using Ubuntu.

I agree! I am a part time trader as well and love my linux office setup, thinkorswim is a great platform, but it isn't really for my needs. I found a great free charting software called 'ChartNexus' that functions well on Linux.

---

### Post by acornblue on 2012-09-12
I have thinkorswim working on Lubuntu 12.04 with jdk1.7.0_07
I've had similar problems to above.  Here is what I did to install and resolve issue:

used sudo to install to /opt/thinkTDA
created a group called thinktda "sudo groupadd thinktda"
added users to thinktda "sudo adduser john thinktda"
add write to group permission "sudo chmod -R g+w /opt/thinkTDA"

maybe its my internet but it take a while for tos to check for updates.

note: i have not verify that tos supports multiusers let alone simultaneous multiusers.

---

### Post by acornblue on 2012-09-13
if you see out of memory java errors, please increase it.  I've set mine as such, "sudo sysctl -w kernel.shmmax=64000000" and have not seen anymore oom errors.

---

### Post by GouZi on 2012-09-17
> **coldaspetr said:**
> 
Basically I noticed it worked when it installed, guessing because it had sudo privileges. 

Right on!
Looks like TOS needs root privileges to run.

I updated the Main Menu Shortcut. With Unity:
Dash Home > Main Menu

Look for the thinkorswim icon > Properties.

Change:
```
/bin/sh "/usr/local/thinkorswim/thinkorswim"
```

Into:
```
/usr/bin/gksudo /bin/sh "/usr/local/thinkorswim/thinkorswim"
```

---

### Post by GouZi on 2012-09-21
I found using gksudo being a bit cumbersome: always forced to put my password.

However to not require TOS to be run as root, just don't install it as root. Tho following worked for me:

```
mkdir $HOME/TOS
./thinkorswim_installer.sh #Note: there's no sudo here!!!!
# Tell the installer to install in $HOME/TOS
```

No need to gksudo anymore. \o/

---

### Post by octalman on 2013-05-03
You don't have to install Oracle Java to run ToS.  It will run on the openjdk that comes with 12.04, but you must disable the ToS startup ("splash") screen.  If you can't do that, or don't know how, call Tech Service and ask them to disable the splash screen for your account.  I have been using ToS this way since early- or mid-December, 2012.  It crashes occasionally, but it can be restarted easily.  Of course, you can also install Oracle's Java 6, but the last time I checked (March, 2013 ?), they had announced that Java 6 would no longer be supported.

---

### Post by runawaykinms on 2013-11-04
I was able to get it to work for me. I noticed that at installation it worked correctly and I was able to log in to the program. I believe it worked the first time because I used sudo to run the installer. Therefore, I figured I must open the program with sudo privileges. Therefore I did the following:

1. Find where the program file is

In the terminal type: whereis thinkorswim

The terminal should return something like (thinkorswim: /usr/local/bin/thinkorswim

2. Use Sudo to open the above file

sudo /usr/local/bin/thinkorswim

3. Enter your sudo password

The program should open up now with sudo privileges and therefore should work.

Hopefully this will help others!

***By the way, I am on Ubuntu 13.10****

---

### Post by acornblue on 2014-04-29
update: On Lubuntu 13.10 right now. I was unable to run thinkorswim v.1860.9 with Oracle JDK1.8.0_05. Downgrading to Oracle JDK1.7.0_55 works still. Note: thinkorswim now check if we are using openjava & aborts. kernel.shmmax=33554432

---

### Post by CVGH on 2014-05-07
How about tos on Ubuntu 14.04 {64bit}?
Oracle Java 7 from the Webupd8 ppa,12GB RAM.

Starts fine but mouse clicks are "off target" and its
very laggy. Eventually everything works fine.

I've played with this file but does not seem to help:

```

-Xmx1280m
-Xms1280m
-Dsun.java2d.noddraw=true
-Dawt.useSystemAAFontSettings=false
-XX:MaxPermSize=128m
-Djava.util.Arrays.useLegacyMergeSort=true
-classpath/p launcher-first.jar

```

---

### Post by CVGH on 2014-06-22
Now tos totally locks up up the desktop and I have to go to the "alt-F2" terminal
and use top to kill it.

I can't tell if the last Ubuntu or tos update broke it....

---

### Post by CVGH on 2014-09-13
Switching to KDE fixed it. Unity is the problem...

---

### Post by GouZi on 2014-09-18
FWIW, on 14.04:
Installing just openjdk-7-jre (sudo apt-get install openjdk-7-jre) thinkorswim would not launch, it get stuck at "installing updates".

Installing oracle jdk made it work:
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer

mkdir $HOME/TOS
chmod 755 thinkorswim_installer.sh
./thinkorswim_installer.sh
./TOS/thinkorswim/thinkorswim

```

I'm using unity and I have the Nvidia drivers installed.

Also work with gnome-session-fallback, Ubuntu Classic (Compiz) session.

If you have a lot of windows, tweaking the vm options can give you more room performance wise:
edit TOS/thinkorswim/thinkorswim.vmoptions

Replace the lines containing:
```
-Xmx512m
-XX:MaxPermSize=128m
```

by:
```
-Xmx1024m
-XX:MaxPermSize=256m
```

---

### Post by CVGH on 2014-09-21
I gave it lots of RAM:

-Xmx4096m
-Xms2046m
-XX:MaxPermSize=1024m

I'm thinking it's somethiing to do with
the Raedon drivers?

I only have trouble with the login screen, it's like the mouse cursor is "off" by many pixels...
After I get in it's great!

I'll take a look at gnome-session-fallback..

---

### Post by hooverist on 2014-10-07
I am new to Linux - testing out Ubuntu 14.04, Mint 17 and Zorin 9 for three weeks finally got ThinkorSwim working. From what I have been able to determine is it worked fine on earlier versions of Ubuntu as a Java program - TDameritrade has made some changes in the past few years and this is no longer the case. I have tried the majority of the suggestions offered on this and other boards with no success. For me - I would get the installing updates screen and it would hang there (white color) then starting again same screen, but black color. Never would get to log on screen. Tried Wine with exe file - it didn't work either . . . BUT THEN tried PLAYONLINUX it's a little glittchy, but runs pretty good on all three versions. Best on Ubuntu and plus side Charts on my second monitor are better resolution than Windows 7 - two days now - I have not fired up Windows at all.

---

### Post by CVGH on 2014-10-11
I now have installed KDE and tos runs much better. 
Still a bit of a pain to login, but after that runs ok. 
Get the infrequent java error but mostly good.
Seems like a graphic issue....
I do also run it in a windows7 VM so I can watch
CNBC. Never thought of trying wine actually....

---

### Post by jim85 on 2015-01-25
I'm a new-bee
In a new Ubuntu 14.04 32 bit install in a Dell Latitude D430 2-GB RAM, I was able to get Think or Swim running using suggestions in two links:
1) For Java 7: [http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html) 
2) Install & run ToS: [http://www.strategic-options.com/insight/thinkorswim-on-ubuntu-14-04/](http://www.strategic-options.com/insight/thinkorswim-on-ubuntu-14-04/)
From Terminal, running 
/usr/local/bin/thinkorswim
 It would give me the error:
Prism-ES2 Error : GL_VERSION (major.minor) = 1.4
and hang at the login.  After rebooting I get the same error but the program seems to run fine.
BTW:  be sure to run 
sudo apt-get install oracle-java7-set-default

Any ideas about the Prism... error?
Thanks, Jim

---

### Post by kinggoddard on 2015-07-16
Thanks for the update

---

