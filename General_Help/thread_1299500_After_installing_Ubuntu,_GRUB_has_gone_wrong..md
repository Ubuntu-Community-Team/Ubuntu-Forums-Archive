---
title: "After installing Ubuntu, GRUB has gone wrong."
date: 2009-10-23
forum: General Help
---

### Post by Ocarina on 2009-10-23
Hello, normally I can fix my own PC problems, but I'm not familiar enough with Linux, so to anyone that could help, I would appreciate it, thank you.

This is all the info, sorry if it's a bit long:

About a year ago I installed Ubuntu 8.4(working fine) on my PC, then I upgraded my PC(new motherboard, processor, that sort if thing) and I also installed Windows 7 in my new build.

Recently, I was reading about Ubuntu again and realised they have brought out Ubuntu 9.10. So I thought I would try it out, I tried to install it through windows, but when I tried to use it, but that didn't work properly(another story, however it did show up in GRUB and gave me the option to choose either Windows 7 or Ubuntu in a BOIS/DOS screen). So I decided to install it on another partition without Windows help.

Now this is where it gets hard to explain. I don't have a working DVD Drive, it broke, so to install it, I put it on a USB memory stick, however, I couldn't get it to boot from the BOIS, so through Windows I chose the option to get it to boot the installer without the BOIS. If you can remember there's, an option to do this if you start it through Windows.

So, I restarted and then it brought up the normal GRUB screen, asking me to choose Windows 7 or Ubuntu again. I chose Ubuntu and the proper installer started, I chose work along side other partitions, so it wouldn't delete Windows 7. It finished and said it would restart the PC.

Now this is where it gets odd. after I turned on my PC, GRUB was "different", it said "GRUB loading" and lasts for about 30 seconds, then says "there's an unknown error, or something along those lines". Then it brings up a screen, with these options(I could be wrong but it's close to this):
Ubuntu 9.10
Ubuntu (recovery mode)
Memory Test
Memory Test (recovery mode)



That's it, I don't know what to do, I think it's a different version of GRUB, I don't get this, can someone please give me a hand.
If there's something you don't understand or I got wrong, just ask.

Thank you.

---

### Post by blwizard on 2009-10-24
I don't know exact solution to your problem because I don't really understand your problem. But one thing I know is that 9.10 uses ext4 as the default filesystem, and grub doesn't support booting from ext4 partitions. So during install, you have to make /boot a separate partition with ext2 or ext3 filessytem. Hope it helps.

I don't use windows, so I don't know how you could "through Windows I chose the option to get it to boot the installer without the BOIS", but anyway this is probably not related to your problem.

---

### Post by Ocarina on 2009-10-24
> **blwizard said:**
> I don't know exact solution to your problem because I don't really understand your problem. But one thing I know is that 9.10 uses ext4 as the default filesystem, and grub doesn't support booting from ext4 partitions. So during install, you have to make /boot a separate partition with ext2 or ext3 filessytem. Hope it helps.
Thanks for your reply. The problem is Windows, I can't start Windows 7, or even Ubuntu.
Normaly, I would get a GRUB screen asking me if I want to start either Windows or Ubuntu, but after I tried to fully install Ubuntu on another partition, it gave me this odd and different version of GRUB.
Here's what happens:

GRUB Loading.
error(unknown error)"title"

Then, I get this option screen:

GNU GRUB v.197 beta3

Ubuntu, Linux 2.6.31-10-generic
Ubuntu, Linux 2.6.31-10-generic(recovery mode)
Memory test(memtest86+)
Memory test(memtest86+, serial console 115200)

Could you please tell me if there's anything I can do, or type in to GRUB to fix this, Thanks.

---

### Post by Ocarina on 2009-10-24
If you could just help me start Windows, that would be great.
I could download a partition program to fix this, or something along those lines.

Thanks again.

---

### Post by ranch hand on 2009-10-24
> **blwizard said:**
> I don't know exact solution to your problem because I don't really understand your problem. But one thing I know is that 9.10 uses ext4 as the default filesystem, and grub doesn't support booting from ext4 partitions. So during install, you have to make /boot a separate partition with ext2 or ext3 filessytem. Hope it helps.

I don't use windows, so I don't know how you could "through Windows I chose the option to get it to boot the installer without the BOIS", but anyway this is probably not related to your problem.
I have no idea where this information comes from but it is wrong.  Both versions of grub, .97 (grub-legacy) and 1.97beta4 (grub2) fully support ext4.

I have been running 9.04 on ext4, with grub .97 since the 9.04RC came out.

---

### Post by ranch hand on 2009-10-24
For a start I would try the recovery mode, I hope you have the RC and not beta 9.10.

If you download another ISO, get the current daily build.

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

The RC came out 2 days ago.  This is a long time in testing.  Been a lot of updates.  The current daily will be better.

I am not an expert when it comes to Win Jerry Lewis Pro.  Won't have it on my box.  However, if you get into a terminal in recovery, running this;
```

sudo update-grub

```
should get the menuentry for MS on the screen menu when you reboot.

While you are on the terminal you should also run;
```

sudo apt-get update

```
and
```

sudo apt-get upgrade

```
This will get any updates installed on you 9.10.

I would also, if you get to the recovery menu, select the dpkg option for checking for broken packages.  I am sorry but I just do not remember the name used on the menu.

---

### Post by Ocarina on 2009-10-24
This is Ocarina, speaking from Ubuntu!

Thanks for lending a hand... Ranch Hand, however, that was not the problem, as it turns out, GRUB had a couple of faults in it:

1. It had no idea what Partitions had Operating systems on them, I installed Ubuntu on my "C: drive"(AKA: hd0) and the second partition(AKA:hd0,1), Windows 7 is on the first one, of course. GRUB thought Ubuntu was on "hd1,5" for some reason.
2. It didn't know Windows was even there until I updated it with Ubuntu, after I finally got it to work.

I'm relieved that my PC hasn't died on me, and all my files are intact. I was wrong about something by the way, I've actually never used GRUB until now, the other program I was using before this was "Windows Bootloader", so you can guess I had no idea what to do, when I actually installed Ubuntu on another partition and not through windows.

Anyway, I'm glad I've fixed my own problem. In the end, this has given me more PC skills other than just in Windows.

Thanks blwizard and Ranch Hand, for trying to help, I appreciate it.

---

### Post by ranch hand on 2009-10-24
This is great.  Glad it works.

Please mark the thread solved (top of this page under "thread tool").

This will make life easier for other folks on the forums.
EDIT
I forgot;
Welcome to Ubuntu

---

### Post by Ocarina on 2009-10-26
> **ranch hand said:**
> This is great.  Glad it works.

Please mark the thread solved (top of this page under "thread tool").

This will make life easier for other folks on the forums.
EDIT
I forgot;
Welcome to Ubuntu

Yeah, I do hope this helps.

Thanks, I'm sure I'll enjoy using Ubuntu.;)

---

### Post by tuahaa on 2009-10-26
Someone beat me to it =(

Anyway, heres the quote from the release notes for 9.10 RC

> **Other OS options not shown in boot menu when installing with Ubuntu 9.10 RC**

  After installation from the Ubuntu 9.10 Release Candidate, other installed operating systems are not correctly displayed in the boot menu. To correct this, users should run sudo update-grub from the commandline after rebooting to their installed Ubuntu system. ([456776]("https://bugs.launchpad.net/bugs/456776")) 

---

### Post by Ocarina on 2009-10-26
> **tuahaa said:**
> Someone beat me to it =(
Doesn't matter, see if you can help me with this then: [http://ubuntuforums.org/showthread.php?t=1301552](http://ubuntuforums.org/showthread.php?t=1301552)

> **tuahaa said:**
> Anyway, heres the quote from the release notes for 9.10 RC
You can do that, or you can download a GRUB editor.

---

### Post by tuahaa on 2009-10-26
Nope sorry I don't know much about Linux to start off. I only knew the answer to this one because I wanted the read the release notes.

Ah well, I hope you find the solution to your other problem

---

### Post by Ocarina on 2009-10-26
> **tuahaa said:**
> Nope sorry I don't know much about Linux to start off. I only knew the answer to this one because I wanted the read the release notes.

Ah well, I hope you find the solution to your other problem
Yeah, thanks. I don't know much about Linux either, I suppose that's why we're here.
At least, I got Ubuntu started and fixed the main problem, which was getting back into Windows 7.

---

