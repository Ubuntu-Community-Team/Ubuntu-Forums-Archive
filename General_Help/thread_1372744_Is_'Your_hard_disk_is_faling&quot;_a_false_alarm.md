---
title: "Is 'Your hard disk is faling&quot; a false alarm?"
date: 2010-01-04
forum: General Help
---

### Post by Usabent on 2010-01-04
Im sure it is but i dont know. I have windows installed i have no warnings that my hard dsik is failing. I used seatools to check my drive it said it passed. I tried the other tests and they all passed.  Please tell me if its really failing i had windows installed for a long time. My drive is a segat internal drive Please help:)

---

### Post by Sef on 2010-01-04
What leads you to think it is failing?

---

### Post by Usabent on 2010-01-04
> **Sef said:**
> What leads you to think it is failing?
When i startup in ubuntu it says Your hard disk is failing

---

### Post by Miljet on 2010-01-04
Why don't you try to help us to help you? We can't see your screen, so please tell us exactly what message you see and at exactly what point during startup are you seeing it.

---

### Post by dcstar on 2010-01-05
> **Usabent said:**
> When i startup in ubuntu it says Your hard disk is failing

There are already many posts on the palimpset package providing false positives like this in 9.10, do a forum search and see if there is a solution.

---

### Post by Usabent on 2010-01-05
Give me a link please im too lazy and plus theres hundreds of fourms on this topic!

---

### Post by Strongman332 on 2010-01-05
use system >> administration >> disk utility

if it says "disk has many bad sectors" you probably don't have a problem.

click the drive in question on the left hand side of the program then check the box that says do not warn me about this drive.

---

### Post by Usabent on 2010-01-05
So this bug wasnt fixed for a long time? oh and 2 other smart applicaitons said it was failing one said it was the reallcollated sector and the other one said hardware ecc recorverd. I Just reformmatted my drive yesterday. and it took care most of the problem

---

### Post by Usabent on 2010-01-05
Please help me!!!

---

### Post by mocoloco on 2010-01-05
Yes it's a bug and yes the [bug is still around]("https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/413673").  I'm too lazy to keep following it, but I doubt very much that my 1yr old drive is failing.  I can't say for you if it's the bug or a real failure.  Just keep your important data backed up and check the bug thread every once in a while.

---

### Post by Usabent on 2010-01-05
Looks like case is closed i had this drive for 5 years no errors

---

### Post by MooPi on 2010-01-05
If you feel your hard disk is failing you can launch the live CD with a reboot. From ther terminal you can check the file system . ```
sudo e2fsck -n /dev/sda1
```

---

### Post by Usabent on 2010-01-07
> **MooPi said:**
> If you feel your hard disk is failing you can launch the live CD with a reboot. From ther terminal you can check the file system . ```
sudo e2fsck -n /dev/sda1
```
  Heres the info for esfck:
e2fsck 1.41.9 (22-Aug-2009)
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sda1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
Heres the info for sudo fdisk -l:
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001    7  HPFS/NTFS

---

### Post by Usabent on 2010-01-07
Come on people help me i want to try it out so badly!

---

### Post by MooPi on 2010-01-07
Did you install Ubuntu with Wubi ?

---

### Post by MooPi on 2010-01-07
Is this what you see when you boot your computer ?

---

### Post by bodhi.zazen on 2010-01-07
To be honest, it does not matter if your hard drive is failing or not.

The most important point is that you back up your data, to CD or DVD or flash drive.

Then when your hard drive does fail, a day, a month, or a decade from now, you have a back up.

Other then that, you come across as expecting us to spell out for you step by step how to check your hard drive and that you are unwilling to search or read information on your own.

You have not explained with sufficient detail as to what concerns you.

I will give you a link:

[http://www.captain.at/howto-linux-smartmontools-smartctl.php](http://www.captain.at/howto-linux-smartmontools-smartctl.php)

---

### Post by Usabent on 2010-01-07
I havent installed it yet i think my drive isnt failing? agian i used sea tools and everything was fine. all tests passed. reallcolated i used hd pro tune. Reallcoated sector  current: 97 worst 97 threshold 36 and data 157

---

### Post by Usabent on 2010-01-07
I installed ubuntu a few nigths ago it was working and the dual boot screen showed up also then i unstalled it as soon as i saw disk is fialing!

---

### Post by Usabent on 2010-01-07
> **bodhi.zazen said:**
> to be honest, it does not matter if your hard drive is failing or not.

The most important point is that you back up your data, to cd or dvd or flash drive.

Then when your hard drive does fail, a day, a month, or a decade from now, you have a back up.

Other then that, you come across as expecting us to spell out for you step by step how to check your hard drive and that you are unwilling to search or read information on your own.

You have not explained with sufficient detail as to what concerns you.

I will give you a link:

[http://www.captain.at/howto-linux-smartmontools-smartctl.php](http://www.captain.at/howto-linux-smartmontools-smartctl.php)
dude i dont need an opoinon to backup!

---

### Post by bodhi.zazen on 2010-01-07
> **Usabent said:**
> dude i dont need an opoinon to backup!

OK, well then good luck to you then. You have back ups for your data and that is about as good as you can do.

Hard drives work until they fail, you checked the drive from windows, and there is not anything more to do. You can not fix bad sectors.

If you get any error messages, post them back and we can help you with them. If you need any additional links, you have google.

---

### Post by Usabent on 2010-01-07
Guys hurry up

---

### Post by Usabent on 2010-01-07
> **bodhi.zazen said:**
> OK, well then good luck to you then. You have back ups for your data and that is about as good as you can do.

Hard drives work until they fail, you checked the drive from windows, and there is not anything more to do. You can not fix bad sectors.

If you get any error messages, post them back and we can help you with them. If you need any additional links, you have google.
  I DONT NEED YOU TO POST HERE So leave!

---

### Post by -kg- on 2010-01-07
> **Usabent said:**
> I DONT NEED YOU TO POST HERE So leave!

Mighty bold, considering that bodhi.zazen is a Forum System Administrator.  Not to mention that he is one of the most knowledgeable people on this site in things Linux and especially Ubuntu.

> dude i dont need an opoinon to backup!...

...Guys hurry up

In case you didn't realize, you have already been given a load of information on the problem.  This is a *_Community Help Forum_*.  We are all running Ubuntu Linux, and we all run across problems from time to time.  We post here in the hopes that someone can help us resolve these problems.

Ubuntu has told you that your hard drive might be failing.  That's what it is; it *_might_* be failing.  Whether it happens tomorrow, next week, a year from now, or the next 5 minutes, no one can tell; not even the OS and the warning it's giving you.

Sooner or later, Hard Drives fail.  It behooves you to have a backup of your data so that when it happens, you can easily replace the hard drive and recover with little or no data loss.  *_No one_* can fix a hard drive.  When it goes, it goes.

None of us get paid for our help and advice.  It is freely given and we really try.  You need to learn how to _ask_ for support, not demand it.

That, or you can ask for the money back that you spent on all this support.

---

### Post by Usabent on 2010-01-07
Okay since you guys think i need to backup close topic!:(

---

### Post by Usabent on 2010-01-07
> **Strongman332 said:**
> use system >> administration >> disk utility

if it says "disk has many bad sectors" you probably don't have a problem.

click the drive in question on the left hand side of the program then check the box that says do not warn me about this drive.
THis dude already helped me so case closed close topic

---

### Post by emarkay on 2010-01-24
It's a known bug:
[https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136?comments=all](https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136?comments=all)

---

### Post by Usabent on 2010-03-21
Wow been 2 months. I add a 2nd hard drive from my old comp cuz it has already 1 hd. The 2nd hd works fine. No bad sectors found. Installed xp on that hd once. It migth be because i installed xp so many times on  my other hd and found many bad sectors. Now i have 2 hd on ubunt other xp :)

---

### Post by 98cwitr on 2010-03-21
same thing happened when I tried to install 9.10 on my gf's old dell laptop (among other problems). I took the "cheap" route and just left 9.04 on there, running fine. It's a known bug, and a false alarm.

---

