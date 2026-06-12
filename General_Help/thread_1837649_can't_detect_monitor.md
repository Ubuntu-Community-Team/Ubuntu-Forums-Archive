---
title: "can't detect monitor"
date: 2011-09-02
forum: General Help
---

### Post by CryptKeeper777 on 2011-09-02
Yesterday, my Xubuntu crashed. At least I suppose it did; I don't remember the details 'cause there was whiskey involved and I was chatting, so I just booted into OS X a.s.a.p. Booting into Xubuntu doesn't work anymore. The Xubuntu logo is displayed, but after that, the screen just remains black.

With SuperGrub2Disk I could boot into Xubuntu, but only via command line. I could log in and also see my files, so the system itself still works. I tried to load a window manager with "compiz --replace" and "xfwm4 --replace", but I just got the error message "could not detect monitor" (or something like that). 

My system: Xubuntu 11.04 on a MacBook 4 (dualboot with OS X). I never had display problems before, at least not with the laptop screen...

Any suggestions what I can do now?

---

### Post by CryptKeeper777 on 2011-09-03
nobody ANY idea? I'm TOTALLY lost here! :(

---

### Post by mark147 on 2011-09-03
Few days ago I was facing same problems and still not get any solutions.

---

### Post by CryptKeeper777 on 2011-09-03
doesn't sound too good... :( well at least I'm able to save my data. If there won't be an answer, I'll just reinstall the system...

Time to find out how to make a full system backup!

---

### Post by CryptKeeper777 on 2011-09-05
Since there doesn't seem to be another solution, I'll just reinstall Xubuntu. But before that, I'll copy everything to an external HD. Which folders in / can I copy back afterwards to loose as little es possible from the installed stuff, but without causing any problems? Definitely my user folder, but what else? I've installed Compiz for example, and installing Compiz on Xubuntu 11.04 is a pain in the ***, so I'd prefer not having to do that again...

Edit: Since the initial problem didn't get an answer, I've opened a new thread which is about the reinstallation --> [click]("http://ubuntuforums.org/showthread.php?p=11221174#post11221174").

---

### Post by MAFoElffen on 2011-09-05
> **CryptKeeper777 said:**
> Since there doesn't seem to be another solution, I'll just reinstall Xubuntu. But before that, I'll copy everything to an external HD. Which folders in / can I copy back afterwards to loose as little es possible from the installed stuff, but without causing any problems? Definitely my user folder, but what else? I've installed Compiz for example, and installing Compiz on Xubuntu 11.04 is a pain in the ***, so I'd prefer not having to do that again...

Edit: Since the initial problem didn't get an answer, I've opened a new thread which is about the reinstallation --> [click]("http://ubuntuforums.org/showthread.php?p=11221174#post11221174").
I am not familiar with OSX installations of Ubuntu... but am with Ubuntu, Kubuntu, Xubuntu, Lubuntu and X-sessions.

If, while in a command line, does 
```

sudo service gdm start

```
...bring up a graphical session?

---

### Post by CryptKeeper777 on 2011-09-05
> **MAFoElffen said:**
> I am not familiar with OSX installations of Ubuntu... but am with Ubuntu, Kubuntu, Xubuntu, Lubuntu and X-sessions.  What exactly do you mean by "OSX installation"? I natively installed Xubuntu on a separate partition, it's not a virtual installation inside OS X, just alongside OS X on the same MacBook.
> 
If, while in a command line, does 
```

sudo service gdm start

```...bring up a graphical session?Nope, I get the following 'answer': ```
 start: Job is already running: gdm 
```As mentioned in the first post, I tried to start xfwm4 and compiz. I've written down the exact messages I got when I tried that.

"xfwm4", "sudo xfwm4", "xfwm4 --replace" etc. (I've tried them all) give me the following: ```
 (xfwm4: 1587): Gtk-WARNING **: cannot open display: 
``` where 1587 is some kind of ID that gets higher (+1) with every try.

The corresponding variants of "compiz" give me the following: ```
 compiz (core) - Fatal: Couldn't open display 
```I can't provide more diagnostic stuff because I don't know the necessary commands, I haven't been into Linux for long...

---

### Post by CryptKeeper777 on 2011-09-05
Alright, I got myself one, two steps ahead. You gave me new hope that the problem might be solvable without a reinstallation of the whole system, and after googling the real error message ("cannot open display", and not something like "can't detect monitor" as I thought I remembered the first time it appeared before opening the thread; I wasn't smart enough to write it down exactly and my mind tricked me...).

Anyway, I somewhere found the command "startxfce4", so I tried it out. That's the logfile:
```
 [   754.994] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[   754.996] X Protocol Version 11, Revision 0
[   754.997] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[   754.997] Current Operating System: Linux XubuntuMB 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 i686
[   754.998] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-11-generic root=UUID=c20257f5-a25c-4f1e-af5e-6e7234db0ca8 ro
[   755.000] Build Date: 11 August 2011  03:47:56PM
[   755.001] xorg-server 2:1.10.1-1ubuntu1.2 (For technical support please see http://www.ubuntu.com/support) 
[   755.002] Current version of pixman: 0.20.2
[   755.004]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   755.007] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   755.009] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Sep  5 23:34:49 2011
[   755.010] (==) Using config directory: "/etc/X11/xorg.conf.d"
[   755.011] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   755.012] Parse error on line 16 of section InputClass in file /etc/X11/xorg.conf.d/60-synaptics.conf
    "1" is not a valid keyword in this section.
[   755.014] (EE) Problem parsing the config file
[   755.014] (EE) Error parsing the config file
[   755.015] 
Fatal server error:
[   755.017] no screens found
[   755.018] 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[   755.022] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   755.023] 
[   755.024]  ddxSigGiveUp: Closing log 
```"/etc/X11/xorg.conf.d/60-synaptics.conf" is a configuration file for the touchpad which I created according to a blog post I found with google and which also worked fine for some time. The evening my system crashed, however, I tried to enable horizontal scrolling, that's the line 16 in the file causing the problems. I deleted the line and ran "startxfce4", and it actually started! 

But it didn't start up the Xubuntu-XFCE4, instead it started a fresh XFCE4-panel (with the standard XFCE4-colors and all, not the Xubuntu-XFCE4-style with the darker colors and all). So I shut the computer down and booted into Xubuntu (remember, so far I could only boot via SuperGrub2-Disk --> Detect any OS --> ...), and I actually got through to the Login screen.

**The problem I now have is that I can't login.** I enter the password, the screen turns black for a short time (an empty shell with a white horizontal cursor-line in the upper left corner) and then I'm just returned to the login screen...

**EDIT**: After some more googling, I solved the login problem. Turns out the owner of the ~/.ICEauthority file were changed to root, I probably started XFCE4 (see above) with sudo or did some other command with sudo that I shouldn't have. Anyway, I booted to the login screen, switched to a shell (ctrl-alt-F1), logged in and did "chown username:username .ICEauthority". Then I logged out and I could normally login using the graphic login panel.

Problem solved! Thanks for your post. Although it didn't actually solve the problem, it gave me new hope which lead me to the solution.

---

