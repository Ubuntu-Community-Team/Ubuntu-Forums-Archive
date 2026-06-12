---
title: "NTFS partition mounted but no files visible"
date: 2011-05-08
forum: General Help
---

### Post by zen123 on 2011-05-08
Hi everyone,

I would like to pre-emptively apologise for my absolute noobishness in asking this question.

My Windows 7 64-bit laptop crashed completely (not even allowing me to boot into Windows) and I found an article that claimed I could use Ubuntu to back up my data. 

I 'installed' Ubuntu 11 64-bit (from a USB) and managed to successfully mount the relevant NTFS partition that contained all my folders, by simply clicking 'mount volume'. 

However when it loaded up said partition it showed a blank window. Underneath it said that there were 0 items and that there was 104 GB free (out of the 150GB available).

What should I do next? Please help!

Thanks and Regards,
Zen

---

### Post by neu5eeCh on 2011-05-08
Sorry no one with more expertise has responded. Your problem sounds "deep".

My first reaction is this: The Ubuntu CD won't do much more than mount your HD. If you can mount it, that's a "good" sign (at least the HD was recognized). If you're not seeing anything, not so good. You need more than Ubuntu.

I think you're better off considering one of the following:

**1.)** I would start with this: [Open Diagnostics CD]("http://www.volatileminds.net/opendiagnostics/index.php/OpenDiagnostics_Live_CD")  See if you can find out what the heck is going on. You won't know what everything is for or what it does, but you can poke around, access the web to query. As long as you're not writing to the HD, you should be fine.

**2.)**  [SystemRescue CD]("http://www.sysresccd.org/Main_Page") This Distro has gotten me out of some fairly serious scrapes. I always keep a copy on-hand.

**3.)**  [Trinity Rescue Kit]("http://trinityhome.org/Home/index.php?content=TRINITY_RESCUE_KIT____CPR_FOR_YOUR_COMPUTER&front_id=12&lang=en&locale=en/")

**4.)** There's also the [SuperRescue CD]("http://distrowatch.com/table.php?distribution=superrescue"). I've never used this CD, but it's out there.

---

### Post by oklokl on 2011-05-08
[http://cafe.daum.net/candan/HfuW/30](http://cafe.daum.net/candan/HfuW/30)
my cafe.. sysresccd 1.5.2 ->Usage
Only the normal operation 1.5.2 old Version

1.6.0~ partimage 0.6.9 error  ->[http://www.sysresccd.org/forums/viewtopic.php?f=4&t=3839](http://www.sysresccd.org/forums/viewtopic.php?f=4&t=3839)
Size error
1.5.2 normal

---

### Post by zen123 on 2011-05-08
VTPoet, thank you for the help. Unfortunately despite having access to those resources I wouldn't know how to use them in the slightest. 

oklokl, thank you for your suggestion but the website doesn't contain anything in English, and Google Translate is making a mess out of it.

From what I've researched it seems to be the case that because its NTFS I don't have permission to read the files. Would anyone be able to help me how to make it so that I can read them? Because they clearly are there, and Ubuntu's check file system says they are clean.

Please help!

---

### Post by neu5eeCh on 2011-05-08
Hi Zen. You can see them? But you can't read them? Can you copy the files?

---

### Post by zen123 on 2011-05-08
VPoet, I can't see them but when I click properties it says the partition is 30GB full. And if I go to properties and try and change permissions, it reverts back to them and doesn't let me keep them. So I can't see the files but I know they are there.

I've tried using nautilus to change but it doesn't work, and I've tried remounting them various ways but it doesn't work. Its frustrating to know that they are there but can't be accessed!

---

### Post by neu5eeCh on 2011-05-08
> **zen123 said:**
> VPoet, I can't see them but when I click properties it says the partition is 30GB full. And if I go to properties and try and change permissions, it reverts back to them and doesn't let me keep them. So I can't see the files but I know they are there.

I've tried using nautilus to change but it doesn't work, and I've tried remounting them various ways but it doesn't work. Its frustrating to know that they are there but can't be accessed!

Did you try to change the partition in any way prior to having this problem? This sounds similar to a bug which occurs when users try to resize their NTFS partition using GParted.

---

### Post by Anonymous is Incognito on 2011-05-08
Maybe the following helps:

[list]
[*]Installing the NTFS driver:

```
sudo apt-get install ntfs-3g
```

[*]Running nautilus as privileged user:

```
gksudo nautilus
```
[/list]

---

### Post by zen123 on 2011-05-08
VTPoet, I didn't change the partition in the slightest. So I'm truly lost.

And thank you for the suggestion Anonymous, but unfortunately I've tried those things and they aren't working. 

Thank you, please keep the help coming - I'm at my wits' end here!

---

### Post by Anonymous is Incognito on 2011-05-08
Can you get to your data using the command line? 

Then you can copy your data over to your mounted external drive with [FONT="Courier New"]cp[/FONT].

If you come across any permissions issues, be sure to use [FONT="Courier New"]sudo[/FONT]

See:
[FONT="Courier New"]man mount[/FONT]
[Navigating the UNIX filesystem](http://www.ee.surrey.ac.uk/Teaching/Unix/) (tutorial one and two)

---

### Post by zen123 on 2011-05-08
I can get to the partition but the partition says it has 0 files. But in the partition properties it has 30GB used up so the files are there. If I try and change permissions I get nowhere since it reverts back automatically, and even nautilus fails to help :(

---

### Post by Anonymous is Incognito on 2011-05-08
Maybe check out a hex editor to view the data. That however is the last thing that comes to my mind.

```
sudo apt-get install bless
```

```
gksudo bless
```

If this doesn't work, I'd consider the files to be lost.

---

### Post by zen123 on 2011-05-08
Hi Anonymous, thank you for that. What do I do specifically? Type in both those commands in terminal and then try and mount the drive again? Sorry for being so lost!

---

### Post by neu5eeCh on 2011-05-08
You should really consider using the SystemRescue CD. If your partition registers usage, but you can't see files, then it sounds as though your partition table was somehow corrupted. Usually, there's a back-up of the last good partition table. The SystemRescue CD will help you find it and restore it (based on my own experience), but you need nerves of steel.

In reality, this forum probably isn't going to be very helpful. You should register at the [PartedMagic Forum]("http://forums.partedmagic.com/viewforum.php?f=1"). There, you will find users who have the skill level to, possibly, hold your hand. You should also register at the [SystemRescueCD Forum]("http://www.sysresccd.org/forums/"). They will also be much more helpful.

---

### Post by Anonymous is Incognito on 2011-05-08
Apologies,

Unlike it's Windows counterpart WinHEX, which I've used in the past, bless doesn't allow you to browse a disk.

WinHEX is capable of seeing/finding lost files aswell as hidden ones you normally wouldn't get to see. (it allows you to browse $SystemVolumeInformation for instance)

My thought was that other editors could aswell, and now looking at the general feature set, I don't think you could find that functionality.

Sorry for the misplaced hope.

My last advice would be to use data forensic tools. I, unfortunately can't guide you a long way with that. HTG [has helped me](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/) in the past, but I can't offer you anything more than this.

Best of luck, I hope someone else can help you.

---

