---
title: "Won't log in after adding second monitor!"
date: 2010-08-15
forum: General Help
---

### Post by Madwand on 2010-08-15
I'm using Ubuntu Lucid Lynx on my new laptop. After plugging an old VGA monitor into the VGA port to add a second screen, I rebooted as the screen options manager asked me to do. I got to the login screen and typed in my password... Ubuntu tried to restart, then kicked me back to the login screen! This is the correct password. I tried all sorts of things by using "recovery mode" (which is pretty useless) like starting in safe graphics mode (I unplugged the offending monitor also, of course) and tried using backed up xorg.conf file, but nothing works! Do I have to completely reinstall? What changes are made by adding a second monitor? What can I do to fix this? Please help!

Some information on my configuration:
The laptop is a custom Cyberpower Xplorer X6-8500 notebook.
The main display is a Compal NBLB2 Notebook 15.6" Full HD 1920x1080 Display
The second monitor is 1280x1024
The video card is an ATI Mobility Radeon HD 5650 GDDR3 1GB PCIe 3D Video

---

### Post by Madwand on 2010-08-15
Update: I was able to log in text-only by using Ctrl-Alt-f2. I used 'cat .xsession-errors' and the last line says:

.: 34: Can't open /home/<username>/.profile

The .profile file is there and seems to have the correct permissions, so I don't know what's wrong or if this has anything to do with the problem.

Any ideas? A post here describes similar problems:

[http://ubuntuforums.org/showthread.php?t=1553663](http://ubuntuforums.org/showthread.php?t=1553663)

---

### Post by scrooge_74 on 2010-08-15
did you try reconfiguring the xserver? or removing the .profile file?

---

### Post by Madwand on 2010-08-15
> **scrooge_74 said:**
> did you try reconfiguring the xserver? or removing the .profile file?

If by "reconfiguring the xserver", you mean selecting the option that says something about that during a "recovery" session, then yes. (I've tried all those options, although that particular one didn't appear to actually do anything when I selected it). I also tried:

sudo dpkg-reconfigure xserver-xorg

and:

sudo dpkg-reconfigure -phigh xserver-xorg

I don't know what these do, but they didn't help.

Removing my .profile caused me to just go into a screen with just the default Ubuntu background on it (I haven't changed it) and no icons, panels, etc.

---

### Post by chopinhauer on 2010-08-15
> **Madwand said:**
> Update: I was able to log in text-only by using Ctrl-Alt-f2. I used 'cat .xsession-errors' and the last line says:

.: 34: Can't open /home/<username>/.profile


And the other lines? I believe you have only 2 lines in .xsession-errors. Can you run 'gnome-session' from an 'xterm' session?

---

### Post by Madwand on 2010-08-15
> **chopinhauer said:**
> And the other lines? I believe you have only 2 lines in .xsession-errors. Can you run 'gnome-session' from an 'xterm' session?

Trying to run gnome-session gives:

** (gnome-session: 1758): WARNING **: Cannot open display:

I know there is already an X-session loaded, but I don't know how to connect to it.

It's hard for me to get all the lines in my .xsession errors, because I have to type them all in manually. There are only 4 other lines. A couple say"Beginning session setup...". The rest of it is kind of complicated but looks benign. If I could log in, I could paste it for you! This is frustrating!

---

### Post by chopinhauer on 2010-08-15
> **Madwand said:**
> 
It's hard for me to get all the lines in my .xsession errors, because I have to type them all in manually. There are only 4 other lines. A couple say"Beginning session setup...". The rest of it is kind of complicated but looks benign. If I could log in, I could paste it for you! This is frustrating!


Can you get a graphical 'xterm' session (you can choose your session at login)? Or it crashes like all the other? When you have a graphical terminal you should be able to run 'gnome-session' or at least:
```

metacity --replace &
gnome-panel &
nautilus &

```

---

### Post by Madwand on 2010-08-15
> **chopinhauer said:**
> Can you get a graphical 'xterm' session (you can choose your session at login)? Or it crashes like all the other? When you have a graphical terminal you should be able to run 'gnome-session' or at least:
```

metacity --replace &
gnome-panel &
nautilus &

```

I can find no option for getting into any kind of graphical terminal. Only the normal login seems available. I've tried those commands from a text prompt, but X windows isn't available so it doesn't work.

---

### Post by chopinhauer on 2010-08-15
> **Madwand said:**
> I can find no option for getting into any kind of graphical terminal. Only the normal login seems available. I've tried those commands from a text prompt, but X windows isn't available so it doesn't work.

In the lower panel of the greeting screen you can choose the language and session type.

Otherwise you can stop the **gdm** service and launch the session from a terminal:
```

sudo service gdm stop

```
and then either
```

startx

```
or
```

xinit

```

---

### Post by Madwand on 2010-08-15
There is no "languages" option available on the lower bar of the login window, and no way to switch session types.

I tried the "gdm stop" command and it worked... "startx" then switched me to a completely black screen with just a mouse pointer available. This probably isn't what was intended. I don't see anything I can do on this screen. It's not a terminal, just... empty.

---

### Post by chopinhauer on 2010-08-15
> **Madwand said:**
> 
I tried the "gdm stop" command and it worked... "startx" then switched me to a completely black screen with just a mouse pointer available. This probably isn't what was intended. I don't see anything I can do on this screen. It's not a terminal, just... empty.


Probably you have a problem with the **gnome-session** program, CTRL+ALT+BACKSPACE to kill the session and then launch 'xinit'.

---

### Post by Madwand on 2010-08-15
> **chopinhauer said:**
> Probably you have a problem with the **gnome-session** program, CTRL+ALT+BACKSPACE to kill the session and then launch 'xinit'.

Hmm, didn't work. Not even "raising skinny elephants" reboot code is working. I'm going to have to hard reboot.

---

### Post by chopinhauer on 2010-08-15
> **Madwand said:**
> Hmm, didn't work. Not even "raising skinny elephants" reboot code is working. I'm going to have to hard reboot.

You can also go back to your console with CTRL+ALT+F1 and then kill the X server:
```
sudo killall X
```

---

### Post by Madwand on 2010-08-15
I'll try the Ctr-Alt-F1 code if I get stuck like that again. But what else can I try with X not working? It just seems like everything I try goes nowhere. I'm really tempted to reinstall, fortunately I have /home on a separate partition. I'd really like to find a simple fix for what's wrong, though, so I can avoid reinstalling in the future if this happens again. I'd also like to be able to use a second monitor!

---

### Post by chopinhauer on 2010-08-16
> **Madwand said:**
> I'll try the Ctr-Alt-F1 code if I get stuck like that again. But what else can I try with X not working? It just seems like everything I try goes nowhere. I'm really tempted to reinstall, fortunately I have /home on a separate partition. I'd really like to find a simple fix for what's wrong, though, so I can avoid reinstalling in the future if this happens again. I'd also like to be able to use a second monitor!


X starts just ok. Just the clients refuse to start. Start your X with **xinit** so you'll have at least a terminal, then start Metacity and Firefox:
```
metacity --replace&
firefox&
```

Now you can start 'gnome-session' in the xterm and see what errors it gives you.

---

### Post by Madwand on 2010-08-16
Incredible! I'm logged in now... sort of. It's not quite the same as before (using xinit then gnome-session) but it's close. My gnome-session had this output:

GNOME_KEYRING_CONTROL=/tmp/keyring-UQFP1z
SSH_AUTH_SOCK=/tmp/keyring-UQFP1z/ssh
GNOME_KEYRING_PID=1880
GNOME_KEYRING_CONTROL=/tmp/keyring-UQFP1z
SSH_AUTH_SOCK=/tmp/keyring-UQFP1z/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-UQFP1z
SSH_AUTH_SOCK=/tmp/keyring-UQFP1z/ssh

(polkit-gnome-authentication-agent-1:1903): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1903): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

** (bluetooth-applet:1906): WARNING **: Could not open RFKILL control device, please verify your installation

(gnome-power-manager:1902): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.1/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x1952e70'
Initializing nautilus-gdu extension
Initializing nautilus-open-terminal extension
** (nm-applet:1907): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:1907): DEBUG: foo_client_state_changed_cb
** (nm-applet:1907): DEBUG: foo_client_state_changed_cb


So... is it any clearer how to fix this problem? I'd rather not go through this process every time I want to reboot! At least I can cut and paste errors for you now.

---

### Post by chopinhauer on 2010-08-16
> **Madwand said:**
> 
So... is it any clearer how to fix this problem? I'd rather not go through this process every time I want to reboot! At least I can cut and paste errors for you now.


The problem is probably in the **gdm** package, reinstall both it and **x11-common** with a:
```

sudo apt-get --reinstall install gdm x11-common

```

---

### Post by Madwand on 2010-08-16
> **chopinhauer said:**
> The problem is probably in the **gdm** package, reinstall both it and **x11-common** with a:
```

sudo apt-get --reinstall install gdm x11-common

```

Did this and rebooted, trying to log in normally. Still kicks me back to the login screen after a couple seconds of trying to log in. Is there anything else I can try?

---

### Post by chopinhauer on 2010-08-16
> **Madwand said:**
> 
Did this and rebooted, trying to log in normally. Still kicks me back to the login screen after a couple seconds of trying to log in. Is there anything else I can try?


Now that you can obtain a graphical session, you can post the *.xsession-errors* file of a failed session.

---

### Post by Madwand on 2010-08-16
And so I can! The .xsession-errors reads:

```

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/etc/gdm/Xsession: Beginning session setup...
.: 34: Can't open /home/proper/.profile
```

---

### Post by chopinhauer on 2010-08-16
Your session seems to enter in a loop. Do you have any of these files in your home directory: .xsession, .xsessionrc, .Xsession, .Xclients?

Are you sure that all your hidden files (those beginning with a dot) belong to your user?
```

sudo chown proper:proper /home/proper

```
to be sure.

Do you use any automatic login features (automatic login, no password)? Deactivate them with **gdmsetup** and **users-admin** and try logging in.

---

### Post by Madwand on 2010-08-16
> **chopinhauer said:**
> Your session seems to enter in a loop. Do you have any of these files in your home directory: .xsession, .xsessionrc, .Xsession, .Xclients?

Are you sure that all your hidden files (those beginning with a dot) belong to your user?
```

sudo chown proper:proper /home/proper

```
to be sure.

Do you use any automatic login features (automatic login, no password)? Deactivate them with **gdmsetup** and **users-admin** and try logging in.

I do not have any of those .x files you mentioned, although I do have an .Xauthority.

All my hidden files belong to me. This was one of the first things I checked.

---

### Post by Madwand on 2010-08-16
So... my laptop has been out of commission a couple days now. While I've learned some interesting diagnostic techniques, I'm not sure I'm any closer to getting a usable computer. Does no one have any idea what might be wrong? Is my only option to reinstall? That would be disappointing.

---

### Post by oli-UK on 2010-08-17
I have just had a similar problem solved for me - my sincere thanks to [chopinhauer]("http://ubuntuforums.org/member.php?u=1119799")

see this thread for all the details 
[http://ubuntuforums.org/showthread.php?t=1553663](http://ubuntuforums.org/showthread.php?t=1553663)

SOLUTION was to rename /usr/lib/gnome-settings-daemon   
in my case I appended .bak

I could not do this in Ubuntu despite sudo chmod the file and directory so used a bootable live puppy linux CD to rename the file.
I am sure you will find a better way to rename the file.

---

### Post by chopinhauer on 2010-08-17
> **Madwand said:**
> 
So... my laptop has been out of commission a couple days now. While I've learned some interesting diagnostic techniques, I'm not sure I'm any closer to getting a usable computer. Does no one have any idea what might be wrong? Is my only option to reinstall? That would be disappointing.


Did you deactivate automatic login and login without a password? ('gdmsetup' and 'users-admin') I think it is choosing some strange session, but it is difficult to debug if you can't choose your default session at login.

Reinstalling 'gnome-session' and 'dbus-x11' might also be useful, otherwise look into the directories /etc/gdm/PreSession and /etc/gdm/PostLogin if there are other files except Default and Default.sample.

**PS**: the thing I really don't understand in your problem is why **gdm** doesn't tell you that your session lasted less than 10 seconds and offer you a failsafe session like it is supposed to do.

The solution I gave **oli-uk** is a mistake solution. I misread his post and said "Ok, to move this directory", while it is not the right thing to do. And unexpectedly it worked.

---

