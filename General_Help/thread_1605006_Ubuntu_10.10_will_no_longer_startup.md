---
title: "Ubuntu 10.10 will no longer startup"
date: 2010-10-24
forum: General Help
---

### Post by Paulieb on 2010-10-24
I have been dual booting Windows 7 and Ubuntu for a few years now, and yesterday I successfully updated my Ubuntu partition to release 10.10.

Today my daughter visited and used my computer. She always boots into Ubuntu rather than Windows, and today I suspect that she may have turned off my computer before Ubuntu had completed shutting down.

After my daughter left for the day, I started up my computer, selected Ubuntu from my Grub2 menu, and got dumped to a command-line interface with the following lines at the end:

mount: mounting /dev on root/dev failed: No such file or directory

mount: mounting /sys on root/sys failed: No such file or directory

mount: mounting /proc on root/proc failed: No such file or directory

Target filesystem doesn't have requested /sbin/init

No init found. Try passing init= bootarg

I'm thinking that my Ubuntu partition has probably been corrupted and that I will need need to reinstall Ubuntu. If anyone has any ideas as to how I might be able to repair or revive the partition without having to re-install the operating system, I'd be greatly appreciative.

My thanks in advance to anyone who can offer any suggestions.

---

### Post by IMSargon on 2010-10-24
Yeah, the first thing I'd do is see if I really did lose all my stuff. Use an Ubuntu LiveCD to boot up your computer.

Once you're booted up, go to System -> Administration -> Disk Utility

Select your hard drive. Does the SMART status say "Disk is healthy"? Click your Ubuntu partition and then click the "Check Filesystem" button. This will fix any little problems if there are any. Once that's done, click the "Mount Volume" button. Then an icon will appear on your desktop or in Places -> Computer or something. Browse around and make sure you can see all your files. 

If all that seems fine, your problem is not unfixable. Maybe try posting your /etc/fstab file for us. Once you get this far, let us know and we'll come up with some more ideas.

---

### Post by sikander3786 on 2010-10-24
Boot into a Live CD as mentioned above and do a disk check.

```
fsck -f /dev/your-drive
```

You can see your partitions with

```
sudo fdisk -l
```

And then replace 'your-disk' with appropriate 'sda**X**'

Once completed, reboot and see if it worked.

---

### Post by Paulieb on 2010-10-25
Thank you very much IMSargon and sikander3786 for your suggestions. I figured that I would need to do something with an Ubuntu Live CD, but had no idea what that "something" would be. I'll try these suggestions out tonight when I get home from work and then report back on the results.
 
Thanks again to you both, I really appreciate your taking the time to help out.

---

### Post by Paulieb on 2010-10-25
Hi again  IMSargon and sikander3786. Well I tried both of your suggestions to no avail.

Following IMSargon's directions, I saw that SMARTstatus showed my disk as healthy. When I then clicked on the Check Filesystem button, it returned a message that my Ubuntu partition was not clean (whatever that might mean). When I subsequently tried to mount the partition, Ubuntu hung with the little rotating circle going on indefinitely and the partition never mounting.

Following sikander3786's directions, I restarted Ubuntu from the Live CD, went to a terminal session, and ran the [FONT=monospace]"fsck -f /dev/sda6" command, and received a response that my Ubuntu partition was busy or in use by another application.

So...as it now stands, I am unable to mount my Ubuntu partition and browse the files contained there. I cannot therefore tell you what is in my /etc/fstab file.

Is there anything else you can suggest for me short of my reinstalling Ubuntu in my unmountable ext4 partition? Any further suggestions you may have would again be greatly appreciated.

Thanks again.

Paul
[/FONT]

---

### Post by nerdleturtle on 2010-10-25
Perhaps the bootloader was corrupted. Is there anyway for you to repair that?

---

### Post by Patrick M. on 2010-10-25
With live cd in the machine, shut it down and reboot from the live cd. you should get a repair option in the installer. The live cd does not let you see the files on the hard drive. You can also run memtest from the live cd

good luck!

---

### Post by tk189 on 2010-11-11
This is a massive problem and it is cropping up all over the place in numerous threads.

It has plagued me for a couple of months now, first with 10.04 and recently with 10.10. it has got to the point I am seriously considering abandong ubuntu totally. See this thread: [http://ubuntuforums.org/showthread.php?t=1595808](http://ubuntuforums.org/showthread.php?t=1595808) 

I do not dual boot with any Windows version, 100% ubuntu yet daily I have to purge and reinstall Grub2 via the liveCd.

I am not one to mess about i9n the dark depths of systems, I install a few bits and bobs eg apache, php, mySQL (another pain since upgrading as the very useful xampp doesn't work with 10.10) and use it for web design and development work. I pretty much use gedit for editing as each time I have had bluefish installed I have noticed an increase in freezes and subsequent re-boot failures.

Having re-installed 10.10 3 or 4 weeks ago my system has run problem free until yesterday. I had not installed aything new or done anything differently yet the old symptoms first encountered a couple of months ago (10.04) began to manifest.

Sudden lock up of everything including mouse cursor.

If mouse still functions, then none of the launchers including drop down from the top bar to reboot, shut down etc work at all. (all the eye candy continues to work but nothing actually opens or shuts down)

Then having had to press the reset button or switch off power to reboot the boot fails and I get a message ending in Try passing init= bootarg

Then I have to boot from the liveCD, chroot to my installed version and then purge and re-install grub using this technique:  [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Previously before upgrading to 10.10 in the hope the problem had been resolved it got to the point I was having to do this several times a day. Again this is now the same...

I know ubuntu is free so I really have no right to complain but... 

A thing I have noticed throughout various threads mentioning these similar errors is that it seems to affect pcs with dual and quad core processors... I might be wrong but I have 10.04 installed on an ancient piece of crap pc elsewhere in my house and it runs fine, glitch free.... go figure.

Current;y everything is on /dev/sda1/ maybe I need to split the boot to it's own partition I have no idea... user friendly it most certainly isn't and if I was even a tad less computer savvy I'd have given in by now and gone back to Windoze like so many people are going to do. :(

---

