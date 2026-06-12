---
title: "How to run GUI Program as User"
date: 2010-01-01
forum: General Help
---

### Post by zzzBrett on 2010-01-01
I have XBMC running on a computer that I have SSH access to.  Sometimes, I need to restart XBMC for various reasons, but without connecting a mouse / keyboard, I have no way to. How can I issue a command via SSH to run the program on the main display in GUI mode?

---

### Post by PeEllAvaj on 2010-01-01
Have you tried combining sudo with a --display= flag?

I've never used xbmc, but I often start GUI apps with elevated privileges remotely with commands like:
sudo <program> --display=:0

Which tells it to run as root, and to attach the gui to display :0 (which is the default if you have a typical setup).

---

### Post by zzzBrett on 2010-01-01
> **PeEllAvaj said:**
> Have you tried combining sudo with a --display= flag?

I've never used xbmc, but I often start GUI apps with elevated privileges remotely with commands like:
sudo <program> --display=:0

Which tells it to run as root, and to attach the gui to display :0 (which is the default if you have a typical setup).


This is what is get using that

```
$ xbmc --display=:0
Error: unable to open display
FEH.py: cannot connect to X server

```

That seems like a program-specific argument. Is there any method that is more general, for any program?

---

### Post by HiImTye on 2010-01-01
two commands for these types of jobs:
```
gksu -u <user> <program>
```
to run the program as another user
```
gksudo <program>
```
to run the program as root

---

### Post by zzzBrett on 2010-01-01
> **HiImTye said:**
> two commands for these types of jobs:
```
gksu -u <user> <program>
```
to run the program as another user
```
gksudo <program>
```
to run the program as root

The problem isn't running it as a particular user -- I can ssh in to the user that is logged in to the computer running xbmc; the problem is getting it to the correct display.

Output using gksu:
```
$ gksu -u user xbmc

(gksu:3100): Gtk-WARNING **: cannot open display:
```

---

### Post by zzzBrett on 2010-01-01
any other suggestions?

---

### Post by zzzBrett on 2010-01-03
bump

---

### Post by dcstar on 2010-01-03
> **zzzBrett said:**
> This is what is get using that

```
$ xbmc --display=:0
Error: unable to open display
FEH.py: cannot connect to X server

```


He specifically said **sudo**.

---

### Post by zzzBrett on 2010-01-03
> **dcstar said:**
> He specifically said **sudo**.

It was run as root. Any other suggestions?

---

### Post by zzzBrett on 2010-01-05
bump.. i'm sure there is a way to do this! I just can't figure it out.

---

### Post by zzzBrett on 2010-01-09
bump

---

### Post by PeEllAvaj on 2010-01-15
I don't have access to the man page for xbmc (can't find it in google), can you post it?

I would guess that if --display isn't working, then xbmc provides their own flag for setting the display to run on.

---

### Post by zzzBrett on 2010-01-15
> **PeEllAvaj said:**
> I don't have access to the man page for xbmc (can't find it in google), can you post it?

I would guess that if --display isn't working, then xbmc provides their own flag for setting the display to run on.
```

XBMC.BIN(1)                                        User Commands                                        XBMC.BIN(1)

NAME
       xbmc.bin - XBMC main executable

SYNOPSIS
       xbmc.bin [OPTION]... [FILE]...

DESCRIPTION
       This is the main executable that will run XBMC.

   Arguments:
       -fs    Runs XBMC in full screen

       --standalone
              XBMC  runs  in  a  stand  alone environment without a window manager and supporting applications. For
              example, that enables network settings.

       -p or --portable
              XBMC will look for configurations in install folder instead of ~/.xbmc

       --legacy-res
              Enables screen resolutions such as PAL, NTSC, etc.

       -l or --lircdev
              LircDevice to use default is /dev/lircd .

       -n or --nolirc
              do not use Lirc, aka no remote input.

xbmc.bin                                             July 2009                                          XBMC.BIN(1)
```

---

### Post by falconindy on 2010-01-15
Is XBMC the only thing needing an xserver? If it is... Add this to ~/.xinitrc (make the file if you need to):
```
exec /usr/bin/ck-launch-session /usr/bin/dbus-launch --exit-with-session /usr/bin/xbmc --standalone -fs
```
Make sure its executable, and then run:
```
startx -- :0
```
That'll start an X server on display 0 with xbmc on it. If you need to be running multiple instances of X, change the 0 to 1, or whatever display is free.

---

### Post by zzzBrett on 2010-06-18
I never got this working.. is there a generic way to open a program as a specific user on a specific screen?

---

### Post by zzzBrett on 2010-06-19
bump

---

### Post by dadepfan on 2010-06-21
As a reasonably new Ubuntu user, I'd like the answer to this question also.  Even if accessing the Ubuntu machine directly, there should be a way to execute a program (with elevated privileges) from the menu system in Gnome, from the icons on the desktop, or from the launch items on the top panel.  In Windows, you can right-click on items and choose "run as administrator."  Why not be able to do the same in Gnome to run a program with elevated privileges??

My work-around is to add 'gksu' to the command in the properties window for the item on the menu, or for the icon on the desktop.  This makes the change permanent.  There should be a way to do it on-the-fly.

Dave

---

### Post by zzzBrett on 2010-06-21
> **dadepfan said:**
> As a reasonably new Ubuntu user, I'd like the answer to this question also.  Even if accessing the Ubuntu machine directly, there should be a way to execute a program (with elevated privileges) from the menu system in Gnome, from the icons on the desktop, or from the launch items on the top panel.  In Windows, you can right-click on items and choose "run as administrator."  Why not be able to do the same in Gnome to run a program with elevated privileges??

My work-around is to add 'gksu' to the command in the properties window for the item on the menu, or for the icon on the desktop.  This makes the change permanent.  There should be a way to do it on-the-fly.

Dave

That is actually a little different than what I am trying to figure out. But I do agree there maybe should be a "run as root" option in the right click menu--doesn't seem too hard to add.

Anyways, what I am trying to figure out is how to, from ssh, run a command that will cause a program with a GUI frontend to appear in the session on the screen of a user that is already logged in.

---

### Post by dadepfan on 2010-06-21
> **zzzBrett said:**
> 
Anyways, what I am trying to figure out is how to, from ssh, run a command that will cause a program with a GUI frontend to appear in the session on the screen of a user that is already logged in.

Is the logged-in user local or remotely logged in?  Are they on a GUI desktop or at a command line?  This is not something I can answer, but just curious.

I am using NX Client for windows (from NOMACHINE) to connect to my Ubuntu server (running a NX server) over my home LAN.  This allows me to log into the server (headless machine - no monitor, keyboard, or mouse attached) and into the Gnome GUI front end. 

Dave  :p

---

### Post by zzzBrett on 2010-06-21
> **dadepfan said:**
> Is the logged-in user local or remotely logged in?  Are they on a GUI desktop or at a command line?  This is not something I can answer, but just curious.

I am using NX Client for windows (from NOMACHINE) to connect to my Ubuntu server (running a NX server) over my home LAN.  This allows me to log into the server (headless machine - no monitor, keyboard, or mouse attached) and into the Gnome GUI front end. 

Dave  :p

Almost what I'm trying to do--
Situation:
Computer A (Server) - Logged in as User
Computer B  (SSH Client)

User is logged in to Computer A (Server) in a gnome session.
I want to log in to Computer A via Computer B, through SSH as User, and start an application that will appear on the screen of User on computer A.

A little complicated, but it seems like it should be do-able.

---

### Post by K.J. on 2010-06-21
That's something I've never been able to figure out how to do, but here's my work around.  Install x11vnc (sudo apt-get install x11vnc).  You can then run the command (from an ssh term) x11vnc -passwd P@$$w0rd to open up the vnc server (you can set it up to run all the time but I don't recommend that, it's very insecure).

Then you can use any vnc program, like ultravnc on windows, to remote into the GUI.

---

### Post by penp on 2010-10-14
> **zzzBrett said:**
> Almost what I'm trying to do--
Situation:
Computer A (Server) - Logged in as User
Computer B  (SSH Client)

User is logged in to Computer A (Server) in a gnome session.
I want to log in to Computer A via Computer B, through SSH as User, and start an application that will appear on the screen of User on computer A.

A little complicated, but it seems like it should be do-able.
You may have already found the answer for this, but I figured I would go ahead and give you an answer.

```
$ DISPLAY=0:0 xterm
```

Setting the $DISPLAY variable from an ssh shell will allow you to start programs on the X desktop currently running on the system. You can make this permanent for the current shell by exporting the variable.

```
$ export DISPLAY=0:0
$ xterm
$ firefox
```

Of course, the value of DISPLAY will need to be the value of the currently running display, but in most cases this will be 0:0 for a single screen on a desktop.

---

### Post by zzzBrett on 2010-10-14
> **penp said:**
> You may have already found the answer for this, but I figured I would go ahead and give you an answer.

```
$ DISPLAY=0:0 xterm
```

Setting the $DISPLAY variable from an ssh shell will allow you to start programs on the X desktop currently running on the system. You can make this permanent for the current shell by exporting the variable.

```
$ export DISPLAY=0:0
$ xterm
$ firefox
```

Of course, the value of DISPLAY will need to be the value of the currently running display, but in most cases this will be 0:0 for a single screen on a desktop.

No, haven't figured it out yet, but I will try this, thanks!

---

