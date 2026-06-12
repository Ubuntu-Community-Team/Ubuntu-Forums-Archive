---
title: "How to Extract a .run file"
date: 2010-07-21
forum: General Help
---

### Post by MrRichard on 2010-07-21
Hi, I apologies if this has been asked before, but how do you extract a .run file?

This is what I tried to do:

>cd ~/Desktop
>sudo sh ati-driver-installer-10-1-x86.x86_64.run --extract

After entering my password, this appeared:

>sh: Can't open ati-driver-installer-10-1-x86.x86_64.run

What am I doing wrong? It apparently worked in [this thread]("http://ubuntuforums.org/showthread.php?t=370580").

---

### Post by lisati on 2010-07-21
From the thread you mentioned:
> [You don't extract run files]("http://ubuntuforums.org/showpost.php?p=2213351&postcount=2")

Why do you want to extract it instead of running it?

---

### Post by MrRichard on 2010-07-21
> **lisati said:**
> Why do you want to extract it instead of running it?

I installed fglrx (ATI graphics card driver) from Synaptic Package Manager. Everything installed and works fine, except there is a watermark at the bottom right corner of the screen saying that I'm running unsupported hardware.

In the installation instructions, it says that my 5830 should be supported. 

According to a post at [Phoronix]("http://superuser.com/questions/54157/amd-unsupported-hardware-watermark-in-linux-mint"):

[INDENT]With the fglrx 8.39.4 driver (or newer), there's a chance you may run into a watermark (similar to the AMD testing watermark) saying that your hardware is unsupported when in fact it is supported. If you run into this unsupported hardware watermark, it's likely that /etc/ati/control is missing. If that's the case for you, try reinstalling the driver or manually copying the control file. The driver contents can be extracted using the --extract argument and the control file is located in common/etc/ati/.[/INDENT]

I have tried reinstalling the driver via Synaptic Package Manager with no luck.

---

### Post by bigfatgooglefat on 2010-07-22
If I were you, I'd just remove the community driver and install the one strait from ATI. If you wanna install from the .run make sure the file is executable (right click -> properties --> permissions) then run it with ```
sudo /path/to/driver.run
``` with the correct path of course. Then you're guaranteed to have the newest driver and no more watermark when you restart.

---

### Post by MrRichard on 2010-07-22
> **bigfatgooglefat said:**
> If I were you, I'd just remove the community driver and install the one strait from ATI. If you wanna install from the .run make sure the file is executable (right click -> properties --> permissions) then run it with ```
sudo /path/to/driver.run
``` with the correct path of course. Then you're guaranteed to have the newest driver and no more watermark when you restart.

Okay, I uninstalled the community driver, rebooted, ran the .run file, rebooted and found that the driver didn't work on startup like the community driver did.

In the installation files, it said:
[INDENT]If the X Server fails to load on the next attempt, please run 'aticonfig --initial -f' from the console.[/INDENT]

So I entered that exact quote in the terminal and this spewed out from it:
[INDENT]Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-1
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.
[/INDENT]

Any suggestions?

---

### Post by MrRichard on 2010-07-22
Finally! I uncompressed the .run file by entering the following in the terminal:

[INDENT][I]cd /"directory of the file"
sh ati-driver.run --extract "a new directory of your choice"[/I][/INDENT]

I'll reinstall the community driver and replace the missing files shortly...

---

### Post by renkinjutsu on 2010-07-22
> **MrRichard said:**
> Okay, I uninstalled the community driver, rebooted, ran the .run file, rebooted and found that the driver didn't work on startup like the community driver did.

In the installation files, it said:
[INDENT]If the X Server fails to load on the next attempt, please run 'aticonfig --initial -f' from the console.[/INDENT]

So I entered that exact quote in the terminal and this spewed out from it:
[INDENT]Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-1
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.
[/INDENT]

Any suggestions?

when you type the command "aticonfig --initial -f", it should have been run as root

```
sudo aticonfig --initial -f
```
because the xorg.conf is somewhere in the root filesystem, users have no permission to write in that directory

---

### Post by MrRichard on 2010-07-23
> **renkinjutsu said:**
> when you type the command "aticonfig --initial -f", it should have been run as root

```
sudo aticonfig --initial -f
```
because the xorg.conf is somewhere in the root filesystem, users have no permission to write in that directory

Thank-you SO much for the help. The watermark is gone, and everything works more smoothly. :D

---

