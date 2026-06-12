---
title: "Problems with ubuntu on one drive and windows on another."
date: 2011-04-12
forum: General Help
---

### Post by Mikhal4linux on 2011-04-12
I installed ubuntu on my 2nd drive while having windows on the 1st. Now, if I remove the 2nd drive, grub won't load and I can't access windows. How can I remove the 2nd drive (which I want to put into another computer) and still be able to load windows?

---

### Post by lmarmisa on 2011-04-12
Welcome to the Forums.

What version of windows are you using? XP, Vista, 7?.

---

### Post by Hedgehog1 on 2011-04-12
Mikhal4linux,


There are two steps to making this work the way you want.

**lmarmisa** asks about which windows you are running so we can give your the correct 'FIXBMR' steps to make that disk boot directly into windows again (Vista & Windows 7 do it one way, XP does it another way).

To remove the Windows entry on the 'all Ubuntu' disk, boot Ubuntu with only that disk in the computer and then:

```
sudo update-grub
```

Your next reboot of the Ubuntu only computer will not have windows listed anymore.

***The Hedge***

:KS

---

### Post by dragonfly41 on 2011-04-13
Just to add my example that I have Windows Vista (and incidentally ubuntu 10.10) now on separate partitions in my laptop (Dell Inspiron 1720).  The Grub menu shows five boot options.

Then I have a _second_ installation of ubuntu 10.10 on an external USB drive (a drive in an Akasa enclosure) which can be booted as USB device (F12) provided that your bios (F2) allows USB booting.

If your second drive is USB can't you boot into it through F12 .. after fixing your MBR?

In my Dell Inspiron 1720 there is in fact space for a second caddy (HDD2) but I've yet to purchase that and try that setup.

---

### Post by Mikhal4linux on 2011-04-13
Thanks for the replies! I am using windows 7, 32 bit.

---

### Post by Hedgehog1 on 2011-04-14
OK - make sure that just your Windows drive is in the computer, and then do this to get windows booting on it's own again:

You will need a Windows recovery disk.  If you don't have one, you can download the ISO for   [VISTA]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") or [WINDOWS7]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

Boot from the windows 7 / Vista  emergency repair disk, do the following:
[IMG]http://img10.imageshack.us/img10/5826/small51runningrecoveryd.png[/IMG]
[IMG]http://img856.imageshack.us/img856/3690/small52selectingwindows.png[/IMG]
[IMG]http://img826.imageshack.us/img826/3484/small53commandprompt.png[/IMG]
[IMG]http://img215.imageshack.us/img215/9547/small54bootrec.png[/IMG]

You can reboot and Windows will come up again!

***The Hedge***

:KS

---

### Post by Mikhal4linux on 2011-04-15
So, I know this is ubuntuforums and not windowsforums, but now I get a blue screen with windows after it tries to boot up, and system repair said it could not fix it. I'm trying memory test diagnostic, then I'll try the other bits on the repair disk and see if anything helps.

---

### Post by Hedgehog1 on 2011-04-15
This is harder to debug remotely, but here are a few bits of information that may be useful:

While hard drives with Linux installs can be moved from one PC to another successfully (in most cases), hard drives with Windows installs cannot (It has to do with Windows drivers for motherboard chip sets).  So if you moved the Windows hard drive to another machine instead of the one it was built for, you will need to put it back in the system it was originally installed on.

If you did not move the Windows hard drive to a different box, then it all gets screwier. 

> ...I get a blue screen with windows after it tries to boot up, and system repair said it could not fix it. I'm trying memory test diagnostic...

You have already done the logical things I would suggest.  While damaged memory can indeed cause the BSOD (**B**lue **S**creen **O**f **D**eath), another possibility is that if you had any NTFS partitions at all on the 'Ubuntu Hard Drive', Windows might have helped itself to some space on one of them for the Windows swap file.  You can tell if that happened if you find a 'pagefile.sys' sitting in the base directory of any NTFS partitions on the 'all Ubuntu' machine.  Typically Windows deals with that particular issue pretty well on it's own, but that is my best guess at the moment.


***The Hedge***

:KS

---

### Post by Mikhal4linux on 2011-04-15
Now I feel silly for not mentioning this!

What I am really doing is building a better box for my windows rig and putting the ubuntu drive with the leftovers because ubuntu's free and I want to learn how to use it. I put in a new motherboard and processor (ASUS M4A77D and AMD Athlon 64 X2 I know, hard to believe those were better, right!) If windows doesn't like things changing on it, that could be the source of my misfortune. 

In fact, the error details tell me: 
"Unspecified changes to system configuration might have caused the problem.

Repair Action:System files integrity check and repair
Result: Failed. Error code = 0x490
Times taken: 1121429 ms." (measuring it in  milliseconds seems rather ambitious, haha)

What can I do to make windows happy? Are there drivers I can install or some such? Do I need to update my bios?

---

### Post by Mikhal4linux on 2011-04-15
Update:

I tried using a repair I found on a thread on a windows forum where the guy put a new power supply in. No help. Here's the link, though: [windows repair after new power supply]("http://answers.microsoft.com/en-us/windows/forum/windows_7-system/cannot-boot-into-windows-7-after-replacing-power/1db01fae-04a1-43a1-bbc7-45c71e4e6f23").

Again, I know this is ubuntuforums. Should I cease this thread and get onto a windows help forum?

---

### Post by Mikhal4linux on 2011-04-15
Update: chkdsk found no errors on the file system, apparently.

---

### Post by Hedgehog1 on 2011-04-15
Once you have done a motherboard change with a different chip-set, you will need to re-install windows on the 'final hardware configuration' of the new Windows system.

I have never found any other reliable way to get Windows cope with large hardware changes.

In a typical Windows work environment, we do this when someone get a new windows system:  We install windows on a new disk (we typically overlay the OS as shipped with our crippled version) and then install the old drive as drive 'D:' so they can copy their documents to the new drive.

You are now aware of one of the fundamental differences between Linux installs and Windows installs - relocating a disk into a machine that isn't an absolutely identical model isn't really possible with Windows; but it usually works just fine with Linux installs.


***The Hedge***

:KS

---

