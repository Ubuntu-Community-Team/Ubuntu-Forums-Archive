---
title: "GRUB - Random chosen OS versions"
date: 2011-12-23
forum: General Help
---

### Post by snakeboy on 2011-12-23
Hi all,

Recently installed 11.10 from scratch and am encountering a strange issue and have no idea where to even begin troubleshooting:

At boot time I select the default first option. Boots up, I log in and start installing programs and configuring things to my liking.  After a day or two uptime, I reboot follow the exact same login selection and am taken to a "bare" version where all my previous changes have vanished.
I do NOTHING, no changes anywhere, simply reboot again, from the GRUB menu, select the SAME exact option, this time it boots up into the version as it was after my configuring.

I shake my head, a "glitch in the matrix" maybe and proceed.  Make some more changes, reboot, select first option, changes remain, no problems.  All is well for a few days then after a reboot I am returned to a clean version upon login.  Several reboots (ONLY, no changes made anywhere) later I end up back at the version I'm expecting.  Easy to tell as they have different backgrounds.  

Now that I acknowledge that SOMETHING is wrong I've been trying to recreate the conditions that cause things to change.  NOTHING I try can "make" it happen, it appears to occur randomly.  I may get my nicely configured desktop 5 boots in a row, then suddenly I'll get a clean slate version again.  It may stick around for a few reboots until mysteriously it is replaced by the "correct" version.

I need to be clear that I am making NO changes to the system when these changes occur.  Power on, select first option (or let it auto-select first option after timeout) login, version A.  Click shutdown/reboot, repeat procedure EXACTLY and at some point it will randomly select version B.

Why could this be happening and where should I start looking for what could be causing this?

ANY help would be appreciated as I've googled it to death and found nothing useful on this topic.  Apparently I'm the only one experiencing it?

Thanks!

---

### Post by BC59 on 2011-12-23
Do you share /home directories between different systems?

---

### Post by snakeboy on 2011-12-23
> **BC59 said:**
> Do you share /home directories between different systems?

I have a single folder in my home directory that I am sharing as a CIFS client for my router to write it's logs to, but that's the only sharing taking place on this machine.

---

### Post by snakeboy on 2011-12-24
UPDATE:  [SIZE="1"](While most people are celebrating xmas, I'm still struggling with this!)[/SIZE]  After a LOT of trial and error today I managed to find a way to recreate this issue reliably, here's how:

If I reboot the machine by clicking "wheel" icon, select "Shut Down" from the drop down menu then choose "reboot", the system will reboot and on startup I select the first option in GRUB (3.0.0-14-generic)and it will load up the "clean/unmodified" version of 11.10.

However, if I reboot using "**[FONT="Courier New"]sudo reboot[/FONT]**" from a terminal, I reboot, select the first option again in GRUB(3.0.0-14-generic) yet this time I'm taken to my ACTUAL 11.10 configured as I want it.

Strange thing is that doing "**[FONT="Courier New"]uname -a[/FONT]**" in either booted version gives the EXACT same result [COLOR="Black"]**([FONT="Courier New"]linux server 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 i686 i386 GNU/Linux[/FONT])**[/COLOR]

Why would my method of shutdown/reboot have any bearing on my selections at boot up?  Surely no matter how I make the system restart, I should get the SAME kernel/desktop by choosing the SAME choice from the GRUB menu each time?

I hope this information helps someone with more knowledge on how GRUB works point me in the direction of what could be causing this.

---

### Post by BC59 on 2011-12-24
Try this, install grub customizer, run:

```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer
```

and then check from the customizer if there is something to tweak to avoid this problem.

---

### Post by oldfred on 2011-12-24
I think I saw something similar where the poster had his system on a underpowered USB drive. It was resolved by using an external power source not the USB port for power. Drive just took longer to spin up on USB power.

Where is /home on your system, is it the same hard drive as / (root)?

---

### Post by snakeboy on 2011-12-25
Going to install GRUB Customizer and play with that in a moment, thanks BC59!

> **oldfred said:**
> I think I saw something similar where the poster had his system on a underpowered USB drive. It was resolved by using an external power source not the USB port for power. Drive just took longer to spin up on USB power.

Where is /home on your system, is it the same hard drive as / (root)?

Both are on the same drive. It's an IDE drive (not SATA), yet still listed as /dev/sda (?)
Anyway, I had recently installed a second drive, a 250GB SATA drive which is picked up correctly as /dev/sdb.  Although early on in my testing I tried unplugging the second drive to ensure it had nothing to do with the issue, and the problem persisted as before so there's definitely no confusion about where it's booting from.

---

### Post by oldfred on 2011-12-25
Systems with mixed IDE & SATA sometimes have numbering issues. The IDE drive is usually promoted to sda as the BIOS uses the older primary master logic for boot drive. But BIOS totally controls which SATA drive to boot. Do you have jumpers set to primary master or cable select with the "newer" 80 conductor cable for the IDE drive?

---

### Post by snakeboy on 2011-12-25
I installed the GRUP Customizer and have tinkered with it a little but not resolved the issue.  (Although I still like to tinker some more before concluding that it did not help.)

> **oldfred said:**
> Systems with mixed IDE & SATA sometimes have numbering issues. The IDE drive is usually promoted to sda as the BIOS uses the older primary master logic for boot drive. But BIOS totally controls which SATA drive to boot. Do you have jumpers set to primary master or cable select with the "newer" 80 conductor cable for the IDE drive?

It's currently set to Cable Select and it's the "last" device on the cable. Perhaps I should switch it to Primary Master?
With both drives connected, I have this issue, yet if I disconnect the SATA drive the problem persists.  If I enable just the SATA and disconnect the IDE drive, machine won't boot.  No operating system found.

Is it possible that GRUB is using kernel images that it's somehow getting from the SATA drive?  I'm not familiar at all with exactly what GRUB does, ie where it looks to find things and if not where it expects them, what does it do next.
I read elsewhere that uninstalling (apt-get remove) previous versions is the "correct" way to get rid of them.  I did so with the oldest version offered in the GRUB bootup menu, it removed the files from /boot, but the option to select it is still there.  Selecting it boots the current version.

Is there a way I can reinstall GRUB making it add only the version I'm currently "in" as it's only option at boot?
I was under the impression that it would not even offer a menu if you have just one OS (ubuntu) installed, which I do, yet I'm getting the menu each time I boot with nothing but current and previous versions of ubuntu to choose from (and memtest of course).  Is this a clue that GRUB is seeing another OS perhaps on the other drive?  Even though I have disabled "scan for other OS's" in the GRUB Customizer recommended above.

---

### Post by SirWeazel on 2011-12-25
For what it's worth... I would try and narrow down a possible drive order/id issue. I recently found that the drives in my computer would change (sda would become sdb, ect...) depending if I did a cold boot vs a warm reboot.

To help narrow down, you could disconnect all other drives (even cd and usb drives, some printers have drives built in also)

Ubuntu should be using the uuid to mount drives.

This probably isn't your issue, but hey it's a start. At least cross out one possibility.

---

### Post by snakeboy on 2011-12-26
Ok, I believe I've found a solution to this, here's what I did:

I set the IDE drive to Single/Master (jumperless).  I then completely unplugged the SATA drive.  Did a few test reboots and the problem still occurred. I then booted off the Ubuntu 11.10 CD into a "live session".  I then ran "[Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")" using the default settings.  When done, I rebooted from the HDD again and the problem is SOVLED! 

I'm not sure about exactly what Boot-Repair did, but I believe a re-installation of GRUB was what did it.  It's cleaned up my GRUB menu nicely and I only have two options to choose from.  3.0.0-14 and 3.0.0-14 Recovery.  

Now regardless of how I restart the system, the CORRECT version loads.  I then reconnected the SATA drive, corrected the reference to it in fstab and it's working exactly as it should be now.

What a relief!  Thanks to all for tips and pointing me in the right direction.  I hope this saga will help someone else if they ever find themselves with this issue.

:)

---

