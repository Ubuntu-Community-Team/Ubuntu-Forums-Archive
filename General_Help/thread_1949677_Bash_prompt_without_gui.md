---
title: "Bash prompt without gui"
date: 2012-03-30
forum: General Help
---

### Post by electrojustin on 2012-03-30
So I'm leaving town for a while and would like to make my desktop a lag free server. I've tweaked some settings and got runlevel 4 to boot without starting lightdm, however I don't have a bash prompt on it. I did get wifi working and can ssh into my server and use screen and everything, but it would be nice to control it physically before I go rather than find a computer to borrow for remotely controlling something sitting right in front of me. At the moment telinit 4 sometimes produces kernel messages on an otherwise blank screen. Sometimes I can type on the screen, but it isn't bash as no commands work. SSH reveals I am indeed in runlevel 4. Any advice?

---

### Post by Jose Catre-Vandis on 2012-03-30
Why not just undo the tweaks, let it boot to gui login and leave it there. At the machine CTRL+ALT+F* (where * is ~ 1 - 8 ) will get you to a terminal prompt. You should have no problem ssh-ing in remotely and running commands. You have the added benefit, if remoting in from a linux machine of running X apps if needs be. (ssh -X)

---

### Post by electrojustin on 2012-03-31
Well I'm already away so ssh is the only option anyway, however I would like to fix this for the future. I don't actually need to undo the tweaks since default runlevel is 2 and I haven't touched that. I don't want to leave it on the gui login prompt because:
 
1. Leaving X and LightDM running is sort of a waste of electricity and resources when you're going to be away for 10 or so days-I'm running a minecraft server 24/7 while I'm away so efficiency is of upmost importance.
 
2. Correct me if I'm wrong, but don't I need to login to use wifi? I've set up WPA supplicant to connect to my network automatically but I think there is some sort of override because the little wifi applet appears to not work with wpa supplicant in use and with a gui I still use the applet, leaving me to believe I have no connection outside of a bash or XFCE session.
 
As for the X tunneling thing, I borrow the laptop I'm using, so I'm sorta forced to use Vista :\
 
One extra piece of info: I tried adding a startup script that would just run the command "bash" in the hopes of getting a bash prompt. Running telinit 4 gives some verbose startup info and then a bash prompt I can't actually type on.

---

### Post by wojox on 2012-03-31
You want runlevel 3. Why did you pick 4?

---

### Post by electrojustin on 2012-03-31
I don't know, isn't it sorta irrelevant since Upstart treats 3-5 the same as 2? You're thinking SystemV Init.

---

### Post by wojox on 2012-03-31
> **electrojustin said:**
> I don't know, isn't it sorta irrelevant since Upstart treats 3-5 the same as 2? You're thinking SystemV Init.

Well maybe. I have a headless Cent-OS Server I ssh into. It's all cli and runlevel 3. 

You using puTTy I take it?

---

### Post by The Cog on 2012-04-01
If I were to do this, I would edit /etc/init/lightdm.conf and add a line to the startup section to prevent lightdm in runlevel 3, like this:
```
start on ((filesystem
           and runlevel [!06]
           and runlevel [!03]
           and started dbus
           and (drm-device-added card0 PRIMARY_DEVICE_FOR_DISPLAY=1
                or stopped udev-fallback-graphics))
          or runlevel PREVLEVEL=S)

```
Then you can just change the runlevel it boots into between 2 and 3. But I can't remember how to do that on Ubuntu.

---

### Post by Cheesemill on 2012-04-01
> **electrojustin said:**
> As for the X tunneling thing, I borrow the laptop I'm using, so I'm sorta forced to use Vista :\
Not a problem, you can do X forwarding over SSH to a Windows machine.

---

### Post by kevdog on 2012-04-01
> **The Cog said:**
> If I were to do this, I would edit /etc/init/lightdm.conf and add a line to the startup section to prevent lightdm in runlevel 3, like this:
```
start on ((filesystem
           and runlevel [!06]
           and runlevel [!03]
           and started dbus
           and (drm-device-added card0 PRIMARY_DEVICE_FOR_DISPLAY=1
                or stopped udev-fallback-graphics))
          or runlevel PREVLEVEL=S)

```
Then you can just change the runlevel it boots into between 2 and 3. But I can't remember how to do that on Ubuntu.

This is a udev script. This file would be located in /etc/init . I believe it would be thet same syntax

---

### Post by electrojustin on 2012-04-01
@The Cog & Kedog
Thats exactly what I did only I chose runlevel 4. I sorta mixed up 3 and 4 on systemV init and wanted to make ubuntu runlevels the same as systemV (or at least one of them). I also added 4 to the stop on condition as well so I could telinit 4 to test instead of reboot and find I can't do anything. The way you change the default runlevel in ubuntu is create (ubuntu doesn't come with one) a /etc/inittab and add the following line to the top of it:
 
```
 id:4:initdefault:
```
 
@cheesemill
Installing X on a windows machine seems like a lot of work when I'm perfectly comfortable using bash for regular server maintanance (I'm really only changing the server config file and monitoring temperature and RAM usage)
 
@wojox
Yes I am using putty. Cent OS is rpm isn't it? I thought most rpm distros were SystemV Init (at least from my bad experiences with an Arch virtubox) and it was only debian based that use Upstart.

---

### Post by electrojustin on 2012-04-03
bunp?

---

### Post by JKyleOKC on 2012-04-03
> **electrojustin said:**
> I thought most rpm distros were SystemV Init (at least from my bad experiences with an Arch virtubox) and it was only debian based that use Upstart.That was true several years ago, but I believe that a number of non-Debian distros have now accepted Upstart and are switching over to it.

---

### Post by Jose Catre-Vandis on 2012-04-03
This old thread might help a bit:

[http://ubuntuforums.org/showthread.php?t=1723874](http://ubuntuforums.org/showthread.php?t=1723874)

---

### Post by electrojustin on 2012-04-04
> **Jose Catre-Vandis said:**
> This old thread might help a bit:
 
[http://ubuntuforums.org/showthread.php?t=1723874](http://ubuntuforums.org/showthread.php?t=1723874)
 
Interesting...I might try that custom grub menu thing once I get a bash prompt. Also, reading through that thread gives me an idea: maybe it's plymouth sorta just sitting on top of the bash prompt. Running ps -e, I see that I have 3 instances of bash running. If I stop plymouth on my command line runlevel, would anything particularly detrimental happen?

---

### Post by electrojustin on 2012-04-04
I've done some research and think the vt.handoff=7 line in grub.cfg is the problem ([https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/913731](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/913731)). I'm going to make a custom menu entry without it. Does anyone know how to set the default menu entry?

---

### Post by electrojustin on 2012-04-08
Well I feel rather dumb. After getting back from vacation I've discovered ctrl-alt-f1 works. Marking thread as solved...

---

