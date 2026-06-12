---
title: "Freezing issue"
date: 2009-08-31
forum: General Help
---

### Post by strattrpt on 2009-08-31
I have recently installed Ubuntu for the first time and have been unable to use it.

The problem is not something I am qualified to diagnose ... there doesn't seem to be any consistency in the problem, other than the result :  frozen system requiring a hard boot.

My system contains parts from several old Dell computers ... 
 
Pentium 4  2.0Ghz processor
512 Mb RDram
 10 Gb hard drive (master -- running WindowsXP Home)
 28 Gb hard drive (secondary -- running Ubuntu non-concurrently) 
  WUSB54GC wireless internet card from Linksys with teh rt2870 chipset

I ran memtest86 ... no errors 

I am currently running Windows just so I can ger online to figure out the whole situation ...

After I tried ubuntu and had the system-freeze issue, I wanted to try Fedora, but the Ubuntu GRUB installed on sda (which the Fedora GRUB would not) and now I am forced to keep Ubuntui because otherwise I get an "Error 15" and stops the boot process, disallowing me to even use Windows ...

I would really like to either get ubuntu working, or get it off my computer and find something that will work ... please help :-)

---

### Post by tgeer43 on 2009-09-01
I'd like to help you but you really haven't given any meaningful information about the actual problem.

You say:
> frozen system requiring a hard bootIs this during the boot process?
If it's after you get to the desktop then what are you doing/running when the freeze occurs?
Do you see any error messages?
What version of Ubuntu and how are you installing it? (Live CD, Wubi, etc.)

tgeer

---

### Post by strattrpt on 2009-09-01
I installed Ubuntu 9.04 from the live CD ...  with the gnome GUI ...

The other details are where I am getting frustrated ... There is no one module that seems to be causing the issue.  It froze a bunch of times while I was reading through the menus to try to figure out where the modules and programs are in gnome (I usually use KDE format).  There wasn't a program or module running other than the default startup when the computer froze.

Let me give you some more details ... 

I booted the system to Ubuntu and read the list of applications in the applications menu.  I didn't start any of them, just read the pull-down menu from the desktop.  It kept working until I moved the cursor to the next menu to the left, at which point the pull-down menu  opened halfway, and the computer froze.  The menu never finished opening (I gave it 10 minutes) and the keyboard stopped responding at all.  The mouse would still move, but nothing else that I did would cause any response from the computer, so I hard booted it.

I booted back to ubuntu, and gave the system five minutes to complete the boot process (while I made a cup of coffee).  By the time I made my coffee and sat back at my computer, the system was frozen again -- no programs running, and it had not idled long enough to launch the screen-saver ... it just died without running anything.  The mouse would still move, but clicking did nothing, and the keyboard would not respond.  I gave the system another ten minutes to complete any processes that could have been tying it up, causing it to seem dead, but there was no noise from my drives, and no response after ten minutes -- once again I had to hard-boot. 

I gave it another shot a bit later ... booted to Ubuntu.  I waited until the hard drives seemed to have stopped searching for info for the boot, and everything worked fine for a couple of minutes ... I opened the menu, and tried to set my background.  The desplay options screen loaded, so I figured I was fine.  I clicked on one of the default backgrounds (the orange one that was not loaded on the live CD) and it switched to the new background.  I decided I would rather have the original background, so I tried to switch back, and the computer froze ... same problem and resolution as before.

I have tried re-installing Ubuntu ... with the same issue every time.  I checked the live CD for errors, and there were none found.  I ran the Memtest86, with no errors.  I ran a file system check  with no errors.

According to all information I have been able to gather from my system, there is nothing wrong with the Ubuntu software, and nothign wrong with the method or completion of the installation, but it just keeps freezing on me.  I have gotten the system to work for up to ten minutes, but the freeze and hard boot are inevitable.  

I am out of ideas about how to fix it ... I have been asking if there is a simple fix from other forums, but all anyone tells me is that I need to download teh upgrades before they will help me.  I can't get my wireless card up and running (Linksys WUSB54GCv3) and have no hard-wire connection to the internet, so I can't get the updates to my computer to install them.  I am stuck and frustrated by now, and I don't want to destroy my hardware by continually hard-booting the chips (they are already pretty old chips .. some dating back to 1999).

Is there anything I can do?  If there is no solution in Ubuntu, how would I go about removing the GRUB so I can just start over and try something else?  Please help :-)

---

### Post by petrus4 on 2009-09-01
> **strattrpt said:**
> 
Is there anything I can do?  If there is no solution in Ubuntu, how would I go about removing the GRUB so I can just start over and try something else?  Please help :-)

If you've got a Windows startup disk, load that.  Go into the System Recovery Console which will load with that, and enter
```
fixboot
```

That will reinstall the Windows bootloader.

Then go into Windows and use the Windows version of GParted to delete the Ubuntu partition.

As far as Linux distributions are concerned, do not get anything which claims to be, "user friendly."  You will find every one of them to simply be an excessively complex mess which will cause you instability and headaches.

If you want to use Linux, get [Slackware]("http://www.slackware.com/"), and ignore anyone here who tries to tell you otherwise.

Slack is more spartan than Ubuntu, it's true...and you will need to work somewhat harder to get it set up...but the major difference between it and Ubuntu is that with Slack, once you've solved a problem, it stays solved.

---

### Post by P4man on 2009-09-01
well, if its freezing and not supporting either wired or wireless network cards, then I'd be inclined to suggest you try another distro. 

But if you do want to try, then perhaps there are few things to test. Hard freezes often occur due to crappy BIOS's (specifically, broken or incomplete ACPI implementations). You could try disabling linux acpi support, adding "acpi=off" as boot parameter

here is how:

[https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation](https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation)

---

### Post by tgeer43 on 2009-09-01
> **petrus4 said:**
> If you want to use Linux, get [Slackware]("http://www.slackware.com/"), and ignore anyone here who tries to tell you otherwise.
That's right because after all, what could the 903,304 of us possibly know?

tgeer

---

