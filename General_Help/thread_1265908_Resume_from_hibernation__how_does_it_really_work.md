---
title: "Resume from hibernation:  how does it really work?"
date: 2009-09-14
forum: General Help
---

### Post by mavigozler on 2009-09-14
I work with Windows 6.0.6002 (Vista HomePrem SP2) on a 100 GB internal HDD and with Ubuntu 9.04 on both a 2.0 GB stick and a 1 TB USB-connected external HDD.

My BIOS boot order on the HP Pav dv9500t notebook is (1) CD/DVD-ROM drive, (2) whatever device with OS is sticking on the correct USB connection, and (3) internal HDD.

I don't like to do a Windows shutdown because it shuts down my workspace (yes, I know there are workspace management applications for Windows).  Hibernate was created for that purpose, right?

So when I want to switch to Ubuntu on the stick or external HDD, I go into hibernate on the Windows system.  

Now when I re-power the machine, it should follow the boot order, right?  If it found a USB stick or ext HDD with OS, it should boot that, right?  If the BIOS finds the internal HDD (3rd-in-line), it should "boot" (i.e. resume from hibernate) because its state was written to that drive, right?

But that is not what happens.  What happens is that Windows is resumed, regardless of what device with OS is sticking into my USB ports.

If I go through the process of shutting down Windows, then I can start Ubuntu on either the USB-connected stick or external HDD...the expected BIOS boot process.

What am I ***NOT ***understanding about the hibernate and resume-from-hibernate process, and when BIOS gets involved...or not?

---

### Post by CatKiller on 2009-09-14
> **mavigozler said:**
>  What am I ***NOT ***understanding about the hibernate and resume-from-hibernate process, and when BIOS gets involved...or not?

Possibly the difference between Suspend (suspend-to-RAM) and Hibernate (suspend-to-disk). If your computer is suspended, it doesn't boot anything. All the data is still in RAM. The only thing that takes any time is getting the processor in the same state that it was in before.

Hibernate works the way you describe in Linux, but I've never tried it in Windows so I can't tell you how that works.

---

### Post by P4man on 2009-09-14
Try this: hibernate windows. When the machine appears off, unplug the power cord. Wait a minute or so, plug it back in, turn the machine on with usb stick inserted. This wont work on a laptop though, if its a laptop, remove the battery as well, just for testing sake.

Thing is, Windows vista has a hybrid sleep mode. What it does, is write all RAM to disk, but then puts the machine in sleep mode, it doesn't turn it off. It only does so after 30 minutes or whatever you configure. Thats why it resumes so quickly.

By itself, its a neat feature, it combines the best of sleep mode (quick resume) and hibernate (no data loss even after you cut power)  but it gets in the way of what you're trying to do. You can turn off hybrid sleep mode somewhere in the control panel.

BTW, be aware, if you put vista in hibernate, its NOT save to access the disk from ubuntu!

---

### Post by mavigozler on 2009-09-14
> **P4man said:**
> Try this: hibernate windows. When the machine appears off, unplug the power cord. Wait a minute or so, plug it back in, turn the machine on with usb stick inserted. This wont work on a laptop though, if its a laptop, remove the battery as well, just for testing sake.

[LIST=1]
[*] Battery pulled out.
[*] Windows put into hibernate.  All indications of power shutdown shown.
[*] Power cord pulled out for about one minute.
[*] USB stick containing GRUB/Ubuntu inserted.
[*] Power button pressed.
[/LIST]

When the screen lights up, it shows "Windows is resuming..." (or something like that).

When I go to shutdown Windows, with full power off for just 5 seconds (re-start does much the same), then power back up, the USB stick then loads GRUB and all action is off the stick.

There must a RAM that is powered off the little lithium battery that keeps the system clock in time (among other things), and it must set a flag somewhere that Windows was hibernated and that no normal BIOS booting is to be done.  I call that an annoyance.

> Thing is, Windows vista has a hybrid sleep mode. What it does, is write all RAM to disk, but then puts the machine in sleep mode, it doesn't turn it off. It only does so after 30 minutes or whatever you configure. Thats why it resumes so quickly.

Windows does have a sleep mode, but this is running power through the CPU at a lower power.  This much I know.  The hibernate mode is supposed to be a full power down, except for the possibility that small RAM or PROM running off the little battery must have a flag set specifically for Windows and which overrides normal BIOS booting, right?

> By itself, its a neat feature, it combines the best of sleep mode (quick resume) and hibernate (no data loss even after you cut power)  but it gets in the way of what you're trying to do. You can turn off hybrid sleep mode somewhere in the control panel.

The BIOS is a Phoenix concoction, and I think there must be a setting in BIOS that specifically looks for a "hibernate" flag setting and bypasses the normal boot device polling.  I will check that now.

> BTW, be aware, if you put vista in hibernate, its NOT save to access the disk from ubuntu!


I am not sure what you mean.  I know that hibernation in Vista pretty much saves the image of Windows as it appears in physical and virtual (page disk) RAM and probably the point from which execution is to begin.  I assume all such OSes that make use of a hibernation mode essentially freeze the state and insert a JMP instruction.

What I probably should do is to save the workspace that I want ot preserve so I don't have to remember all the apps and docs I had open when I decided to interrupt the work.  Hibernate was supposed created for the purpose of saving a single workspace so work could resume quickly.

---

### Post by P4man on 2009-09-14
> **mavigozler said:**
> [LIST=1]
[*] Battery pulled out.
[*] Windows put into hibernate.  All indications of power shutdown shown.
[*] Power cord pulled out for about one minute.
[*] USB stick containing GRUB/Ubuntu inserted.
[*] Power button pressed.
[/LIST]

When the screen lights up, it shows "Windows is resuming..." (or something like that).

So you don't get a BIOS splash screen first? heh, are you sure you don't have a second battery in there lol?

Well, if what you say is true, and the machine was fully powered down, then I agree with you, vista is somehow coordinating the hibernation with the BIOS. Windows 7 doesnt do so on my (desktop) machine, when I resume from hibernation (after cutting power), I get a normal BIOS splash screen, my grub bootloader, and only then if I select windows, does it start resuming, so i figure its a feature of your laptop/bios. Perhaps you can disable it somewhere in the bios?

> There must a RAM that is powered off the little lithium battery that keeps the system clock in time (among other things), and it must set a flag somewhere that Windows was hibernated and that no normal BIOS booting is to be done.  I call that an annoyance.

Sounds like it..
> 
Windows does have a sleep mode, but this is running power through the CPU at a lower power.  This much I know.  The hibernate mode is supposed to be a full power down, except for the possibility that small RAM or PROM running off the little battery must have a flag set specifically for Windows and which overrides normal BIOS booting, right?

More or less. Actually sleep mode does turn off your cpu, but it keeps the RAM alive on battery power, and possibly some other peripherals like USB or network, so you can wake the machine up over network or a USB device. But thats also true for hibernate. If you enable wake on lan, the lan card is never truly powered down.


> I am not sure what you mean.  I know that hibernation in Vista pretty much saves the image of Windows as it appears in physical and virtual (page disk) RAM and probably the point from which execution is to begin.  I assume all such OSes that make use of a hibernation mode essentially freeze the state and insert a JMP instruction.


Yes, but the problem is that the filesystem isn't synched. Therefore, its unsafe to mount the ntfs partition from ubuntu (and by default, it wont let you mount it, or only as readonly perhaps). Its as if windows is still running.

---

### Post by mavigozler on 2009-09-14
So I looked at the BIOS.  HP authorizes its customers to use a Phoenix BIOS with an extremely simple interface.

I found something about "Processor C4" option that can be enabled or disabled, but a google search shows it is related to voltage levels in sleep mode and disabling/enabling would not serve my purposes.

One other thing:  the BIOS states "Factory Installed OS"  with the value "Vista".  Thus, the BIOS is made aware of its operating system, which I find interesting.  I don't recall seeing that before.  If the BIOS is made aware of its OS, then perhaps it looks at parameter RAM for that flag to check if hibernate is set or not before doing the boot device polling.

I am not sure if using an alternative BIOS is possible, useful, and risk-free, with relation to its effects.

---

### Post by P4man on 2009-09-14
> **mavigozler said:**
> 

One other thing:  the BIOS states "Factory Installed OS"  with the value "Vista".  Thus, the BIOS is made aware of its operating system, which I find interesting.  I don't recall seeing that before.  If the BIOS is made aware of its OS, then perhaps it looks at parameter RAM for that flag to check if hibernate is set or not before doing the boot device polling.

Yep, might well be it. Try changing it.
BTW, BIOS are almost always OS aware. Thats one of the problems with linux, oem's write their bios so it works with XP and Vista, and all too often, don't give a rat about any other OS. As a result, getting ACPI to work on linux can be challenging.

> I am not sure if using an alternative BIOS is possible, useful, and risk-free, with relation to its effects.


ooph.. I wouldn't dare that. If its even possible, i very much doubt its risk free. After spending a week trying to install an alternative firmwire on a spare fon router, and another week trying to unbrick it after a botched attempt, I decided thats the sort of stuff is out of my league :)

---

