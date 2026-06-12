---
title: "Booting LiveCD and garbled screen afterwards"
date: 2012-09-12
forum: General Help
---

### Post by andy_blah on 2012-09-12
I have tried running a 12.04 LiveCD recently, and before I even get to select between Live mode or installation this is what shows up on the screen:

[IMG]http://i.imgur.com/OSNtD.jpg[/IMG]

The CD stops spinning, and no further signs of activity from the PC, only thing that can be done is unplug. I could try installing it using the alternate CD, but I only plan to use the Live CD as this isn't my PC.

My specs:
[IMG]http://i.imgur.com/vEFCV.png[/IMG]

---

### Post by newb85 on 2012-09-12
Sounds like a graphics card issue.  I had similar issues on a friend's computer a couple years ago, and fortunately thought to write down how I solved it.  Give it a try:

When you boot from the CD, one of the first screens you should see will have small images of a man and a keyboard.  At that screen, hit Esc.  The old-school boot menu should appear.  Select English (or whichever is most appropriate in your case) and hit Esc. again to drop into the CLI.

Enter the command

```
$ live-install xforcevesa
```

Note: this should start the installer.  If you hit "Quit", it will leave you in a Live Session.

---

### Post by coffeecat on 2012-09-12
> **andy_blah said:**
>  I could try installing it using the alternate CD, but I only plan to use the Live CD as this isn't my PC.


If you only intend using it on this PC, but need to run a live session, there's another possibility. Create a live USB with persistence. Boot up with it but log into a virtual terminal. You need to be connected to the internet so it'd be easier to use an ethernet connection. Then, after doing a "sudo apt-get update", install the nvidia-current and nvidia-settings packages with apt-get. Hopefully, the proprietary nvidia driver will be happier with this GPU than the default nouveau driver seems to be.

If you need help with the details, post back.

---

### Post by andy_blah on 2012-09-12
Thank you both for your swift replies. ^^

 > **newb85 said:**
> Sounds like a graphics card issue.  I had similar issues on a friend's computer a couple years ago, and fortunately thought to write down how I solved it.  Give it a try:

When you boot from the CD, one of the first screens you should see will have small images of a man and a keyboard.  At that screen, hit Esc.  The old-school boot menu should appear.  Select English (or whichever is most appropriate in your case) and hit Esc. again to drop into the CLI.

Enter the command

```
$ live-install xforcevesa
```

Note: this should start the installer.  If you hit "Quit", it will leave you in a Live Session.
 

I tried your solution but the 2nd time I press Esc, after the confirmation message, the creen turns blank, and for a short period "boot =" then some more text shows up, but quickly dissapears. Afterwards it loops back to the (human) = (keyboard) screen, and then to the trainwreck that happens afterwards ^^;

 > **coffeecat said:**
> If you only intend using it on this PC, but need to run a live session, there's another possibility. Create a live USB with persistence. Boot up with it but log into a virtual terminal. You need to be connected to the internet so it'd be easier to use an ethernet connection. Then, after doing a "sudo apt-get update", install the nvidia-current and nvidia-settings packages with apt-get. Hopefully, the proprietary nvidia driver will be happier with this GPU than the default nouveau driver seems to be.

If you need help with the details, post back.

This method might suit me better as I'll need to install some libraries. Define "with persistance". Also is 1GB enough for this?

---

### Post by grahammechanical on 2012-09-12
Have you tried pressing F6 and selecting nomodeset and then pressing esc? That may get you to a live CD session.

Regards.

---

### Post by andy_blah on 2012-09-12
Should I press F6 when I'm in the (human)=(keyboard) screen or boot menu?

EDIT: Ignore the dumb question above. I've tried checking the nomodeset option and it still loops.

---

### Post by andy_blah on 2012-09-12
I've got the persistence LiveUSB working, it booted properly but I have no idea how to boot in CLI mode only. I can access the TTYs, but I can't complete what coffeecat said in time, as the GUI keeps on loading and eventually even when in TTY the garbled screen appears (only made out of text this time)

---

### Post by coffeecat on 2012-09-12
> **andy_blah said:**
> I've got the persistence LiveUSB working, it booted properly but I have no idea how to boot in CLI mode only. I can access the TTYs, but I can't complete what coffeecat said in time, as the GUI keeps on loading and eventually even when in TTY the garbled screen appears (only made out of text this time)

Try booting into recovery mode. There won't be an entry for recovery mode in the live session menu (accessible by tapping any key when the purple screen with small small icons at the bottom appears), but when you see the menu press F6 (if I remember correctly) to edit the boot options. Remove "quiet splash" in the kernel line and also "$vt_handoff" if it's there and add "recovery nomodeset".

Warning - I've never tried to get recovery mode in the live session before so I'm not sure whether this will work. I've taken "recovery nomodeset" from the standard grub.cfg file from an installed 12.04 system, but if they don't work, try "single" instead.

If that does succeed in getting you booting up into recovery mode from the live USB, then hopefully you will see the menu that gives you the "drop to root shell with networking" choice. If you do that you'll get a root shell from which you should be able to run apt-get.

Let us know how you get on. I'll be interested to see if this works.

Alternatively, have you tried the nomodeset option alone as grahammechanical suggested?

---

### Post by andy_blah on 2012-09-12
I've tried for the first time, it all went well until it stalled for more than 30 minutes. The line was saying something in regards to doing a checksum on a file with the extension .casperfs (I didn't get to note it down), sorry
. I had to reboot since somebody else needed the PC at that time and that person couldn't take no for an answer -.-

I tried later, same command, and I get this:

Authentification failed.

And it stalls. I rebooted and tried again:

Begin: Adding live session user... ... pwck: cannot lock /etc/passwd; try again later 

[ TTY2 says this: EXT2-fs (loop1): warning: mounting unchecked fs, running e2fsck is recommended.]

How could I run that when I can't even boot Ubuntu properly. X.X

Now ever time I reboot, the same thing happens as above.
I suppose rebooting 2 times wasn't really good for the USB's filesystem...

---

### Post by coffeecat on 2012-09-12
> **andy_blah said:**
> The line was saying something in regards to doing a checksum on a file with the extension .casperfs (I didn't get to note it down), sorry

The casper-rw file is the persistence file. The live USB stick is actually formatted FAT32 - all the files that make up the live USB are in a FAT32 filesystem. The casper-rw file itself contains an ext2 fileystem and that filesystem contains all your persistence files - settings, updates, installed software, etc. Its because of the FAT32 filesystem filesize limit that persistence is limited to 4GB.

Anyway... The fact that it was doing what sounds like a filesystem check on casper-rw (which I've never seen happen) and the other things you've seen suggests the system on the USB is corrupted. Or perhaps the FAT32 filesystem is damaged - it's a fragile filesystem.

I suggest you start over with a fresh live USB, perhaps with a different USB stick. It could just be that the USB stick itself is failing.

**EDIT**: I also found this as an option:

[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)

That's using a live CD but using a USB stick at the same time for the persistence. Personally, I'd prefer the more straightforward option of a single live USB with persistence, but I offer that as another choice.

---

### Post by andy_blah on 2012-09-13
I tried to format and then to re-do the liveUSB, but it was indeed corrupted as you said as unetbootin crashed when it got to install the bootloader. I got another USB (that I initially tought I don't have) and everything went well. I don't suppose it went into recovery mode as Gnome loads up, only this time at 1024x768 instead of the native resolution. I still can't do much of anything. I reached out the terminal and tell apt-get to update, after a few moments the screen gets bedecked with bars. I try again, when I launch the terminal - instant bar screen. I try again and swich to the first TTY, instant garbled text. It isn't any better with the CD unfortunately.

---

### Post by andy_blah on 2012-09-13
I've tried now to find a way to kill either X or to kill Gnome:

When I try the three finger salute (Ctrl + Alt + Backspace) it doesn't do anything. I tried typing xkill in a TTY and this is what it said

```
xkill: Unable to detect display "" 
``` 

This message also keeps showing on the TTY:

```
[147.728861] EXT2-fs (loop1): error: ext2_lookup: deleted inode referenced: 98413 
``` 

Numbers differ though and they keep on showing up one by one.

---

### Post by andy_blah on 2012-09-14
Now all TTYs become littered with ext2_lookup errors. I can't shut X at all, otherwise it bounces right back with the graphical mode. Can anyone suggest what to do? Maybe I could use a different distro that could help me with this? I'm getting full of restarting and trying things with no use. -.-

---

### Post by andy_blah on 2012-09-17
*bump* Anyone?

---

### Post by cariboo on 2012-09-18
I have an Nvidia 6150LE PCI graphics card, the only way I can get it to boot the Live CD is to do what grahammechanical, suggest back in post #5. When you see the Little man & the keyboard, press any key to see the menu. Select your language, and once at the menu screen, press F6, and use the arrow keys to scroll down to nomodeset, then press either the space bar to select. Press esc, then press enter. It will take a few minutes, but eventually you should have a working desktop.

---

### Post by andy_blah on 2012-09-18
And I tried explaining that doesn't work. The desktop shows up properly in a non-native resolution but at random the screen goes garbled again, depending on what app I start, or what shows up in the terminal.

What I also tried today was to ad xforcevesa at the boot command screen, it helped by kicking me directly to a TTY, but the screen still gets littered with garbage after a few minutes of usage. I don't even have time to update the drivers.

---

