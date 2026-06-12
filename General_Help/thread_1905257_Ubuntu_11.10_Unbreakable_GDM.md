---
title: "Ubuntu 11.10: Unbreakable GDM"
date: 2012-01-06
forum: General Help
---

### Post by N1GHTS on 2012-01-06
I have worked with Xorg and older versions of Ubuntu before. It was easy to stop Xorg from running. It seems that in Ubuntu 11.10 it is literally impossible. I have googled this topic furiously for hours trying all sorts of logical methods to tell Xorg to stop running but nothing seems to work.

The reason I need to tell it to stop running is because I am trying to install a new graphics card with a different brand (Radeon to Nvidia) and apparently Ubuntu refuses to boot up to desktop with the new card long enough for me to deal with its driver. When I did manage to switch to console with the new card, the proprietary Nvidia drivers refuse to install while X is running. 

I simply need to break Xorg long enough for me to do my installation and revert it when I am done. Any ideas? Remember, I tried everything. :P

---

### Post by bluexrider on 2012-01-06
sudo stop lightgdm

---

### Post by N1GHTS on 2012-01-06
$ sudo stop lightgdm 	
stop: Unknown job: lightgdm

Awww... and I was so excited too since I haven't tried that yet. Just for fun I tried "sudo stop gdm" and that was also an "unknown job". Any other ideas? :)

---

### Post by bluexrider on 2012-01-06
Might try 
Alt + PrtScn/SysReq + K

---

### Post by Marcelo Ruiz on 2012-01-06
What about login in recovery mode, uninstalling the ATI drivers, then rebooting, login in back in recovery mode and try installing the nvidia-drivers? I usually login in recovery mode to install the Nvidia drivers because the nouveau drivers are broken (since Maverick) and I can't get to a working desktop after a fresh install or booting from the Live CD.
I hope it helps!

---

### Post by N1GHTS on 2012-01-06
[LEFT]I figure Alt-PrintScreen-K is a keyboard shortcut to "sudo kill <current process>" since it seems to work the same way.

And just like "sudo kill", pressing that key combination while in the desktop results in being booted to the graphical Ubuntu login screen. Pressing it repeatedly does nothing productive. Pressing Alt-F1 and doing the same key combination causes the terminal to clear and show the terminal login prompt. 

Either way, since I am trying to install Nvidia drivers and it requires booting up straight to terminal, my ideal solution should be somewhere along the lines of editing some configuration file or type up some un-registration command so that gnome is disabled.

Anyone know what files I need to edit or command I need to execute to make Ubuntu 11 desktop stop running? :confused:
[/LEFT]

---

### Post by N1GHTS on 2012-01-06
> **Marcelo Ruiz said:**
> What about login in recovery mode, uninstalling the ATI drivers, then rebooting, login in back in recovery mode and try installing the nvidia-drivers? I usually login in recovery mode to install the Nvidia drivers because the nouveau drivers are broken (since Maverick) and I can't get to a working desktop after a fresh install or booting from the Live CD.
I hope it helps!

How does one go into recovery mode without grub? This computer I am working with was installed automatically by the Ubuntu 11 Installer disc and has no other Operating system on it, so apparently it didn't install grub.. or at least I don't know if it did. What should I do in this case?

---

### Post by bluexrider on 2012-01-06
While booting, after the BIOS has finished, press the Esc key to enter the recovery prompt.

---

### Post by N1GHTS on 2012-01-06
> **bluexrider said:**
> While booting, after the BIOS has finished, press the Esc key to enter the recovery prompt.

I have tried this 4 times in a row. Every time trying more and more aggressively. No matter how long I tap or hold down the escape key, Ubuntu GUI will still start up. I have found that holding it down slows down its start-up process not to mention the annoying beeping the computer makes when the keyboard buffer reaches capacity. 

Anyway, as usual this is another dead end for me. Should I consider installing GRUB or something? If so, I have no idea how to do that. Either way it seems like overkill for something that at first seems like such a simple thing to do... :confused:

---

### Post by stylishpants on 2012-01-06
> **bluexrider said:**
> sudo stop lightgdm

It's not "lightgdm", it's "lightdm".  Only one "g".

Can't you switch to a virtual console after boot to modify files there?

Ctrl-Alt-F5 to switch to virtual console 5, then you can log in and do stuff.  When you're done just reboot.

X runs on virtual console 7, you can switch back there if you want to with "Ctrl-Alt-F7".

---

### Post by Basher101 on 2012-01-06
i think i killed it once with ```
sudo stop service lightgdm
``` or something of that sort...but it was with the "service" i am sure of it

---

### Post by bluexrider on 2012-01-06
> **stylishpants said:**
> It's not "lightgdm", it's "lightdm".  Only one "g".

Can't you switch to a virtual console after boot to modify files there?

Ctrl-Alt-F5 to switch to virtual console 5, then you can log in and do stuff.  When you're done just reboot.

X runs on virtual console 7, you can switch back there if you want to with "Ctrl-Alt-F7".
That's my fault. (FFS) Fat Finger Syndrome

---

### Post by N1GHTS on 2012-01-06
> **stylishpants said:**
> It's not "lightgdm", it's "lightdm".  Only one "g".

Can't you switch to a virtual console after boot to modify files there?

Ctrl-Alt-F5 to switch to virtual console 5, then you can log in and do stuff.  When you're done just reboot.

X runs on virtual console 7, you can switch back there if you want to with "Ctrl-Alt-F7".


OK so that worked. Its good to know for the future. Unfortunately it does not help me in this specific situation.

So I pull out my old video card, install the new one, wait for the computer to start up, it freezes at a purple screen with a working mouse cursor. Keyboard commands fail to do anything (I cannot switch to a console with ALT-F2 because the computer is completely crashed)

I do this several times, each time trying different tactics to get to the CTL-ALT-F1 or CTL-ALT-F2 screens. Sometimes I am successful (Rarely), but it still crashes after the Ubuntu start-up sound effect. 

Bottom line: I need a way to configure my computer so that the "lightdm" service is unregistered at boot-up so I can install my NVidia drivers. Then I need to re-enable it to see if it works.

How can I go about doing this? :)

---

### Post by stylishpants on 2012-01-06
I see, so you cannot actually complete the boot to get to the point of being able to switch to a virtual console.

In that case, you should boot into single-user mode.  Get a grub prompt during startup.  Access the entry you want to boot, then press "e" to edit it.  Add the word "single" to the end of the line that specifies which kernel to access.

Then boot.  It should come up in text mode with a root user shell.  Many services will be unavailable, including networking.

---

### Post by N1GHTS on 2012-01-06
> **stylishpants said:**
> I see, so you cannot actually complete the boot to get to the point of being able to switch to a virtual console.

In that case, you should boot into single-user mode.  Get a grub prompt during startup.  Access the entry you want to boot, then press "e" to edit it.  Add the word "single" to the end of the line that specifies which kernel to access.

Then boot.  It should come up in text mode with a root user shell.  Many services will be unavailable, including networking.

Is there a way to do this without GRUB? I don't think I have grub installed on the computer I am dealing with. If I need to install grub, how should I go about doing that?

---

### Post by cgroza on 2012-01-06
How about telinit?

```

telinit 3

```

[http://en.wikipedia.org/wiki/Runlevel#Ubuntu](http://en.wikipedia.org/wiki/Runlevel#Ubuntu)

---

### Post by stylishpants on 2012-01-06
> **N1GHTS said:**
> Is there a way to do this without GRUB? I don't think I have grub installed on the computer I am dealing with. If I need to install grub, how should I go about doing that?


It would be very weird if you did not have grub already installed.  It's the default boot loader for Ubuntu 11.10 and most (all?) previous versions.

---

### Post by N1GHTS on 2012-01-06
> **cgroza]How about telinit?[/QUOTE]

I went to CTRL-ALT-1, logged in, typed "sudo telinit 3". It did not complain. I rebooted. I was greeted by the Ubuntu Desktop. Am I missing something?


[QUOTE=stylishpants said:**
> It would be very weird if you did not have  grub already installed.  It's the default boot loader for Ubuntu 11.10  and most (all?) previous versions.

I installed this installation from CD without manually configuring the partitions. It asked me if I wanted to let it configure it for the entire hard drive and I said "sure why not". It was the first time I ever let Ubuntu do that (Normally I do things manually but on this computer it didn't need any special treatment).

As a result, there is no sign of a GRUB boot loader when I turn on the computer. It just jumps straight into Ubuntu. I have tried so many hot keys on boot-up that I've lost track of them all. So If I had to guess, there is no GRUB. If Grub is the only possible way to break Xorg, then I must know how to install and configure grub just to install NVidia drivers. 

I am thankful that my old video card still works. I can't imagine what would happen if I was given a computer with a bad video card and had to replace it with a different brand like this situation. I've been professionally fixing computers for a decade and this is the first time I've had so much trouble installing drivers for any computer on any operating system. Its been over 24 hours so-far and every effort has been a dead end. :|

---

### Post by cgroza on 2012-01-06
> **N1GHTS said:**
> I went to CTRL-ALT-1, logged in, typed "sudo telinit 3". It did not complain. I rebooted. I was greeted by the Ubuntu Desktop. Am I missing something?

You will have to edit this file: /etc/init/rc-sysinit.conf .

At the end of the file, there should be something like this:
```

    # Switch into the default runlevel
    telinit "${DEFAULT_RUNLEVEL}"
end script

```This puts your system into the default runlever, which is 5 when X is started.
Add this line right above those lines so it becomes:

```

    # Switch into the default runlevel
    DEFAULT_RUNLEVEL=3
    telinit "${DEFAULT_RUNLEVEL}"
end script

```Don't forget to backup your old file of course.
Also, this may boot you into the mode you want, but I think it will break your recovery mode since it overwrites the default runlevel variable.

To revert back, just replace this file with the backup.

---

### Post by N1GHTS on 2012-01-06
> **cgroza said:**
> You will have to edit this file: /etc/init/rc-sysinit.conf

You got me excited for a second! I thought I finally got this problem solved... but then it didn't work :sad::sad::sad::sad::sad::sad::sad:

The file was there. I edited it exactly as you described with runlevel 3. Saved the file. Rebooted. And Ubuntu GUI was there laughing at me! Afterwards, I checked the spelling of the script and all looks exactly as you typed it (same number of spaces, capitalization, everything).

[COLOR=Red]
[/COLOR] [URL="http://www.youtube.com/watch?v=bETCusT5kNM"][COLOR=Red]**Here is a 7 minute video of me and the Ubuntu GUI.**[/COLOR]
[I]
"The GUI came back the very next day
The GUI came back... I thought it was a gonner but..
The GUI came back, it just couldn't stay awayyyy"[/I][/URL]

---

### Post by lykwydchykyn on 2012-01-06
> **N1GHTS said:**
> You got me excited for a second! I thought I finally got this problem solved... but then it didn't work :sad::sad::sad::sad::sad::sad::sad:

The file was there. I edited it exactly as you described with runlevel 3. Saved the file. Rebooted. And Ubuntu GUI was there laughing at me! Afterwards, I checked the spelling of the script and all looks exactly as you typed it (same number of spaces, capitalization, everything).


You successfully got into runlevel 3.  There is an old convention that runlevel 3 is configured not to start X11 by default.

Debian, and thus Ubuntu, don't follow that convention.  So while you successfully got to runlevel 3, it didn't do anything for you.

What you need is exactly what the "recovery mode" boot option is for.  I maybe missed it in all the posts, but did you try this?

---

### Post by N1GHTS on 2012-01-06
> **lykwydchykyn said:**
> You successfully got into runlevel 3.  There is an old convention that runlevel 3 is configured not to start X11 by default.

Debian, and thus Ubuntu, don't follow that convention.  So while you successfully got to runlevel 3, it didn't do anything for you.

What you need is exactly what the "recovery mode" boot option is for.  I maybe missed it in all the posts, but did you try this?

If I could it would have been done a long time ago. Every Ubuntu installation I have ever worked with has a GRUB boot screen. This one does not seem to have it, or if its there I don't know how to enable the boot screen. This one was installed completely automated by the latest Ubuntu live CD so if this was a "convinience" thing, I think they screwed up big time.

Are you saying that GRUB is the only way to break Xorg's boot-up script? If so, what should I do to get Grub installed? Frankly I don't care at this point if I rename the entire **/etc** folder to** /etc-still-wont-work** as long as I get a command prompt. I don't need network connectivity. I just to install an offline driver.

---

### Post by sffvba[e0rt on 2012-01-06
From [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode) - 

> NOTE: Users of Ubuntu Karmic (9.10) and higher will need to **press and hold the left Shift key instead of Escape** in step 4, and may not see the "Grub loading, please wait..." message in step 3. 

Try that to access the grub menu.


404

*PS - Thread moved to General Help*

---

### Post by lykwydchykyn on 2012-01-06
> **N1GHTS said:**
> If I could it would have been done a long time ago. Every Ubuntu installation I have ever worked with has a GRUB boot screen. This one does not seem to have it, or if its there I don't know how to enable the boot screen. This one was installed completely automated by the latest Ubuntu live CD so if this was a "convinience" thing, I think they screwed up big time.

Are you saying that GRUB is the only way to break Xorg's boot-up script? If so, what should I do to get Grub installed? Frankly I don't care at this point if I rename the entire **/etc** folder to** /etc-still-wont-work** as long as I get a command prompt. I don't need network connectivity. I just to install an offline driver.

Try what not found just posted.  You can also just telinit to runlevel 1 ("sudo telinit 1") which would take you directly to runlevel 1 from whatever runlevel you're in.  Or do what you did to get to runlevel 3, and change it to runlevel 1 instead.

"recovery mode" is basically runlevel 1 a.k.a. single user mode.

---

### Post by N1GHTS on 2012-01-06
> **not found said:**
> From [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode) - 

Try that to access the grub menu.

I did not know this and it is very helpful. UNFORTUNATELY, this method has several issues.

1. If you hold down the shift key, it will say "GRUB Loading...". If you let go of Shift at this point, it will forget the whole thing even happened and boot to Ubuntu.

2. Keeping the shift key pressed, It takes me to the GRUB menu and I then use the keyboard to select "recovery mode". Once it loads the recovery mode menu the keyboard no longer responds to any keystroke. Not even the number lock light will toggle. The only option is to reboot.

3. At this point I figured out that it might be due to the fact that my keyboard is USB. So I went looking for a spare PS/2 Keyboard and thankfully this computer had a PS/2 jack so I tried again, this time with a PS/2 Keyboard. Now the recovery menu was responsive and I proceeded to the command option (4th menu item). 

When I was finally at the command prompt, I logged in and tried to install the NVidia drivers. It complained that the /tmp folder was read only (it claimed that the file system was in read-only mode). I tried "sudo nano" to edit various files and it turned out to be automatically read only. I even "su" into root and that too had no access to changing files. So much for recovery mode.

I'm back to where I started. This is clearly the devils work. :twisted:

---

### Post by cgroza on 2012-01-06
At the first screen you get in recovery mode, you can select the fsck option and it will exit read-only mode when it is done.
I remember having some problems a few days ago and I encountered the same difficulty as you did.

---

### Post by N1GHTS on 2012-01-07
> **lykwydchykyn said:**
> Try what not found just posted.  You can also just telinit to runlevel 1 ("sudo telinit 1") which would take you directly to runlevel 1 from whatever runlevel you're in.  Or do what you did to get to runlevel 3, and change it to runlevel 1 instead.

"recovery mode" is basically runlevel 1 a.k.a. single user mode.

This did not work. Run level 1 was a mode in which the video card would turn on and off repeatedly... there was essentially no video.

I also tried Run Level 2, but that was the exact same thing as run level 3 apparently.

Your advice was a dead end to me yesterday.

---

### Post by N1GHTS on 2012-01-07
> **cgroza said:**
> At the first screen you get in recovery mode, you can select the fsck option and it will exit read-only mode when it is done.
I remember having some problems a few days ago and I encountered the same difficulty as you did.

So Yesterday I did manage to get into recovery mode without it being read only, except the way I did it was very similar to your advice, except much less elegant. Basically, as soon as I selected recovery mode from GRUB, I held down Control-C and eventually after lots of hammering of that key combination it eventually broke the grub script and placed me in a command terminal without the read only restriction.

Whose bright idea was it to have a read only recovery mode anyways?

Either way, turns out my Nvidia card was broken all along, which is why it was failing to start up with Ubuntu. I learned this only after completely dumping Ubuntu and installing Windows. It had similar problems.

---

### Post by Marcelo Ruiz on 2012-01-08
Try to press and hold down SHIFT to display the boot menu.

---

