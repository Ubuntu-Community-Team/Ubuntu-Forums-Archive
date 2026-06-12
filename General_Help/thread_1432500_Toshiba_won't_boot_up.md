---
title: "Toshiba won't boot up"
date: 2010-03-17
forum: General Help
---

### Post by tnimxunil on 2010-03-17
I was trying to fix my audio driver so that my speakers would work after installing Linux Mint 8. I rebooted it to see if it worked but the computer won't boot up. It gets past the toshiba screen and the mint logo shows up like normal, but then I get what I think is an error message. I can't be sure though because the screen is not showing a solid picture. If I hit escape, I get another similar screen. If I hit escape again the screen goes blank and I can no longer get it to do anything. I'm new to Linux and not much of a computer wiz. Does anyone know how to fix this?

---

### Post by MooPi on 2010-03-17
Do you remember what you did prior to this problem. What did you do to fix your audio ?

---

### Post by tnimxunil on 2010-03-17
I tried a few things:

First, someone recommended this code:

sudo killall pulseaudio
sudo pulseaudio --system --daemon But I just got this back:

oem@Laptop ~ $ sudo killall pulseaudio
oem@Laptop ~ $ sudo pulseaudio --system --daemon
W: main.c: Running in system mode, but --disallow-exit not set!
W: main.c: Running in system mode, but --disallow-module-loading not set!
N: main.c: Running in system mode, forcibly disabling SHM mode!
N: main.c: Running in system mode, forcibly disabling exit idle time!
E: main.c: Daemon startup failed.

That person didn't reply to my reply so I tried to uninstall and reinstall the driver via a guide post on this forum (I cannot find it right now, but I'll keep trying.) The guide said to reboot, so I did. Then I couldn't get it to start back up again.

---

### Post by MooPi on 2010-03-17
The second portion of your post is confusing me. What is this and what interface are you using to edit this 
[COLOR=Red]W: main.c: Running in system mode, but --disallow-exit not set!
W: main.c: Running in system mode, but --disallow-module-loading not set!
N: main.c: Running in system mode, forcibly disabling SHM mode!
N: main.c: Running in system mode, forcibly disabling exit idle time!
E: main.c: Daemon startup failed.[/COLOR]
Are these just messages in terminal?

---

### Post by tnimxunil on 2010-03-17
That's what popped up in the terminal when I entered the code above.

---

### Post by MooPi on 2010-03-17
Try to restart your computer but hit the shift button to enter the grub menu. While in grub select recovery While in recovery search for the pulseaudio config file and remove from the home dirctory. I don't  have pulseaudio installed on my system but I suspect it will be in .config folder. When this config file is gone the global config file will load on next boot.  basicly you want to search out and delete your pulseaudio config in your home directory.
Possible locations :
[B][I]~/.pulse/daemon.conf
~/.config/pulseaudio
[/I][/B]

---

