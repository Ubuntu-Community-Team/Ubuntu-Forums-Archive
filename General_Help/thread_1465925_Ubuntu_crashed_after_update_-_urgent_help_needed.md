---
title: "Ubuntu crashed after update - urgent help needed"
date: 2010-04-29
forum: General Help
---

### Post by abbood99 on 2010-04-29
Hello everyone,
I am having a Ubuntu nightmare. I am relatively new to the whole Linux thing. I just updated my Ubuntu from the update manager today and after I restarted I keep getting the following error:

**Error: You need to load kernel first.**

My boot menu shows the following: 
[B]GNU Grub version: 1.97~Beta4
Ubuntu, Linux 2.6.31-21-generic
Ubuntu, Linux 2.6.31-21-generic (recovery mode)
Ubuntu, Linux 2.6.31-20-generic
Ubuntu, Linux 2.6.31-20-generic  (recovery mode)
Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic  (recovery mode)
Windows 7 (loader) (on dev/sda1)[/B]

The only two that work are the last two.

So I chose **Ubuntu, Linux 2.6.31-14-generic** and booted normally.

From there I typed actionparsnip's suggested solution (which worked for other people on other versions):
**sudo apt-get clean; sudo apt-get --reinstall install linux-image-2.6.31-21-generic**

As you see I suited actionparsnip's solution to my version.

The command downloaded something and made some fixes/updates and everything and seemed to have worked fine.

The system asked me to reboot, and here I am stuck:
Now the boot menue shows the grup prompt which seems like:

Minimal BASH-like line editing supported...
**sh:grub>**

NOTES: I originally installed Ubuntu alongside Windows 7 using Wubi. I can paste the contents "wubildr.cfg" if this helps.

I had to go back to my Windows 7 to post this. Please helpy me wake up from this nightmare. I have worked day and night to configure Ubuntu to suite my needs :(

I appreciate your help.

---

### Post by bcbc on 2010-04-29
Have you replaced wubildr as per this bug?  [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by abbood99 on 2010-04-30
Thanks bcbc!!!! This worked like magic!!!
You saved me a lot of trouble indeed I salute you from my Ubuntu now (not Windows 7) :)

---

### Post by dino99 on 2010-04-30
if you have some free place on your hdd(s), nothing is better than a real install, wibi install linux into a windows file :lolflag:, real joke.

---

### Post by Rokyking on 2010-04-30
> **dino99 said:**
> if you have some free place on your hdd(s), nothing is better than a real install, wibi install linux into a windows file :lolflag:, real joke.

I wouldn't say it's a "joke". It's great for people who aren't confident enough yet to wipe there windows partition and take the dive. I have introduced many friends to Ubuntu with Wubi, and most recommend it to others because it literally requires no technical knowledge. Usually after a bit of messing around. They come back and ask for help on how to install it and wipe windows. How much better could it get?

---

### Post by abbood99 on 2010-04-30
I came up with a wisdom out of this:

**When your Linux crashes, curse your Windows**

You guys seem lettered about the issue. Do you think I can convert my current Wubi installation into a clean Ubuntu one without losing any configuration?

---

### Post by Rokyking on 2010-04-30
Hey abbood69 yes you can use LVPM.
It has not been thoroughly tested with any versions of Ubuntu later than 9.04 but it might work. 
[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

Report back if it did.

---

### Post by Kejenne on 2010-06-02
Good morning

I have a similar problem with the same level of experience, and would greatly appreciate some assistance to restore my precious Ubuntu! :(

I have not performed any updates, and my Ubuntu loads off a USB. I too am faced with the same error:

**Error: You need to load kernel first.**

My boot menu shows the following: 
[B]GNU Grub version: 1.97~Beta4

Ubuntu, Linux 2.6.31-20-generic
Ubuntu, Linux 2.6.31-20-generic  (recovery mode)
Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic  (recovery mode)[/B]

None of these work - they all request the kernal or say that the file cannot be read, in the case of the first boot option.

I too can get to the minimal BASH-like line **sh:grub>**

But I would not have the first clue what to do with that.

Thank you in advance for your time, I sincerely hope someone can help me.



> **abbood99 said:**
> Hello everyone,
I am having a Ubuntu nightmare. I am relatively new to the whole Linux thing. I just updated my Ubuntu from the update manager today and after I restarted I keep getting the following error:

**Error: You need to load kernel first.**

My boot menu shows the following: 
[B]GNU Grub version: 1.97~Beta4
Ubuntu, Linux 2.6.31-21-generic
Ubuntu, Linux 2.6.31-21-generic (recovery mode)
Ubuntu, Linux 2.6.31-20-generic
Ubuntu, Linux 2.6.31-20-generic  (recovery mode)
Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic  (recovery mode)
Windows 7 (loader) (on dev/sda1)[/B]

The only two that work are the last two.

So I chose **Ubuntu, Linux 2.6.31-14-generic** and booted normally.

From there I typed actionparsnip's suggested solution (which worked for other people on other versions):
**sudo apt-get clean; sudo apt-get --reinstall install linux-image-2.6.31-21-generic**

As you see I suited actionparsnip's solution to my version.

The command downloaded something and made some fixes/updates and everything and seemed to have worked fine.

The system asked me to reboot, and here I am stuck:
Now the boot menue shows the grup prompt which seems like:

Minimal BASH-like line editing supported...
**sh:grub>**

NOTES: I originally installed Ubuntu alongside Windows 7 using Wubi. I can paste the contents "wubildr.cfg" if this helps.

I had to go back to my Windows 7 to post this. Please helpy me wake up from this nightmare. I have worked day and night to configure Ubuntu to suite my needs :(

I appreciate your help.

---

