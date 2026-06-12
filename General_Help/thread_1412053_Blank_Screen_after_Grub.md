---
title: "Blank Screen after Grub"
date: 2010-02-20
forum: General Help
---

### Post by Tigerboy2 on 2010-02-20
sorry if this is in the wrong catagory but i'm new. anyway one day i start my computer and instead of starting normally it comes up with a screen which says GNU GRUB version 1.97~beta at the top. i selected the option Ubuntu, Linux 2.6.31-19-generic as i figured this is what normally loads without being propted in the grub menu, but after this i got the ubuntu logo for a few seconds then my screen goes blank. help!!! my laptop is a hp510.

---

### Post by quixote on 2010-02-22
You're using Karmic 9.10, is that right?  Can you boot into a command line recovery console?  I.e. select the second, "recovery mode", option instead of the first usual one.  (If you try it and want to quit out of it, the command is "halt now" without quotes.)

The important thing to remember is that your computer and your data are all fine.  Judging by the point at which it fails, it sounds like it may be having trouble with your video drivers.  Did anything change on your computer between when it did work and when it stopped working?  New monitor?  Upgrades the night before?  Anything?  Alternatively, maybe grub is pointing to the wrong place and can't find ubuntu, but then I think the error would happen earlier in the process.

---

### Post by Tigerboy2 on 2010-02-22
Hey! thanks for answering...

Yes i am am using karmic 9.10. I did get some upgrades the night before aswell. I tried using the recovery mode but i have no idea how to use it. Also when i select recovery mode i get the message "waiting for root file system...gave up waiting for root device..." does this mean it can't detect my hard drive? after this it says "dropping to a shell!". any advice?

---

### Post by quixote on 2010-02-22
Okay, that's just grub losing it's tiny mind.  Your hard disk is fine, and your video drivers are fine.  What probably happened is that the update included a new kernel, that put a new entry in grub, which then didn't play well with the way you have things set up.

The simplest thing may be to try to use the shell it drops you to.  There are commands to tell grub to look for boot instructions it understands, and to put those in its menu.  It's here in the Grub2 help docs, [command line and rescue mode]("https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode").  Command line stuff is always a bit tedious, and you have to be careful to avoid typos (especially hitting Enter when you shouldn't! :)), but it's actually much the quickest method if it works for you.

I'd give that a try, and if there's a problem, let us know which step tripped you up, and what happened when it did.  At this point, all I could do is reprint the instructions on that page, and they do a better job, plus there's a mountain of other info on grub2.

---

### Post by Tigerboy2 on 2010-02-23
hmmmmm i tried express boot to the most recent kernal and also to boot a specific kernal manually. But every time i put in the command "linux boot/vmlinuz root=dev/sda1 ro" i get the message "Error: out of partition" WHat does this mean?

---

### Post by quixote on 2010-02-23
I've never seen that error message before, so I googled it.  (That's a neat trick I learned from a sysop, by the way.  Just copy as much of the error message as you want, with quotes around it, into the search bar.)  The bad news is, it sounds like it [may be a bug]("http://www.mail-archive.com/grub-devel@gnu.org/msg08914.html").  :shock:   I'm not sure, because I don't understand half of what the [bug report]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/494095") is saying, but whenever you get bad behavior from a command you're doing exactly right, and there's a related bug report ... it's not so good.

The fix I would use is to downgrade to legacy grub.  A bit further down on the same page as the earlier link to Grub2 is [reverting to legacy grub]("https://help.ubuntu.com/community/Grub2#Reverting%20to%20GRUB%20Legacy").

---

### Post by itsjustarumour on 2010-02-24
I downloaded the latest Karmic 9.10 updates about 5 hours ago, just rebooted my laptop for the first time, and I have this same problem.  Also with 2.6.31-19-generic kernel. Intel graphics.  Top of screen shows "GNU GRUB Version 1.97~beta4".  I have no other kernels to try booting to. Trying to boot in "recovery mode" I get the same messages - "waiting for root file system...gave up waiting for root device..." etc.  System now completely knackered.

Can't investigate further at the moment as I'm at work, but just wanted to add my voice to this thread.

---

### Post by quixote on 2010-02-24
Yikes.  This is starting to sound bad indeed.  Can you try downgrading grub to the old version, as per the link earlier?

---

### Post by itsjustarumour on 2010-02-24
OK, got time to sit down now and try and sort this  :)

I'm trying to fix it using the how-to at [https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode) and the section entitled "Using CLI To Boot".

The "set" command gives me a bunch of text, of which I assume this is the important bit:

> root=hd0,1

The "ls" command gives me:

> (hd0) (hd0,5) (hd0,1)

The "set root=(hd0,1)" command seems to work OK, but "linux /boot/vmlinuz root=/dev/sd01 ro" just gives me:

> error: file not found

Am I doing this right - or have I completely got the wrong end of the stick?  :roll:

---

### Post by quixote on 2010-02-24
No, you're doing more or less the right things.  The reason I'm adding "less" is because something is still obviously not working. 

First, "linux /boot/vmlinuz root=/dev/**sd01** ro" looks like a typo.  Shouldn't that be /dev/**sda1**?

Also, make sure it really does point to your vmlinuz file.   You can use ls to check: ```
ls (hd0,1)/boot
```If it's not there, it may be in the root directory up one level: ```
ls (hd0,1)/
```If so, the linux line should read: ```
linux /vmlinuz root=/dev/sda1 ro
```Hope that works!

---

### Post by itsjustarumour on 2010-02-24
@Quixote - thanks for the help.  I feel I'm half way there... :)

> **quixote said:**
> First, "linux /boot/vmlinuz root=/dev/**sd01** ro" looks like a typo.  Shouldn't that be /dev/**sda1**?

Perhaps! I was a bit confused by the instructions as to what X and Y should be (I was thinking X was a 0 and Y was a 1, hence XY should be "01" ... but I guess thats me just getting confused - so (hd0,1) needs to be replaced with sda1 for this bit?

> Also, make sure it really does point to your vmlinuz file.   You can use ls to check: ```
ls (hd0,1)/boot
```If it's not there, it may be in the root directory up one level: ```
ls (hd0,1)/
```If so, the linux line should read: ```
linux /vmlinuz root=/dev/sda1 ro
```Hope that works!

ls (hd0,1)/boot gives me:

> grub/ memtest86+.bin vmlinuz-2.6.31-19-generic config-2.6.31-19-generic abi-2.6.31-19-generic System.map-2.6.31-19-generic vmcoreinfo-2.6.31-19-generic in itrd.img-2.6.31-19-generic

- is that right?

ls (hd0,1)/ gives me:

> lost+found/ var/ etc/ media/ cdrom bin/ boot/ dev/ home/ lib/ mnt/ opt/ proc/ root/ sbin/ selinux/ srv/ sys/ tmp/ usr/ vmlinuz initrd.img

---

### Post by itsjustarumour on 2010-02-24
Aha, I think I'm getting somewhere!

> linux /vmlinuz root=/dev/sda1 ro 

is of course the one I need...

---

### Post by itsjustarumour on 2010-02-24
Quixote, you're the man! =D>=D>=D>  You led the way sir, and for that I am very grateful.

Just to re-cap for anyone else who gets this problem:

The how-to at [https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode) recommends the following commands:

```
set root=(hdX,Y)
linux /boot/vmlinuz root=/dev/sdXY ro
initrd /boot/initrd
boot
```

Due to the relevant files actually being up one level in the root directory, the commands I actually had to put in to fix this (one line at a time) were:

```
set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro
initrd /initrd.img
boot
```

Thanks again!

---

### Post by Tigerboy2 on 2010-02-25
YESSSSSSSSSSS!!! i can confirm that that [itsjustarumour]("http://ubuntuforums.org/member.php?u=209646")'s method worked for me aswell. thankyou **VERY** much [itsjustarumour]("http://ubuntuforums.org/member.php?u=209646") and [quixote]("http://ubuntuforums.org/member.php?u=133668")!!

---

### Post by itsjustarumour on 2010-02-25
> **Tigerboy2 said:**
> YESSSSSSSSSSS!!! i can confirm that that [itsjustarumour]("http://ubuntuforums.org/member.php?u=209646")'s method worked for me aswell. thankyou **VERY** much [itsjustarumour]("http://ubuntuforums.org/member.php?u=209646") and [quixote]("http://ubuntuforums.org/member.php?u=133668")!!

@Tigerboy2 - glad you got it sorted!  :)

---

### Post by quixote on 2010-02-25
Glad it worked!  There's a way to do everything in unix / linux / ubuntu.  The trick is finding out *how* ... :-?  Thank the Ubuntu docs, not me :D.

By the way, Tigerboy2, as the original poster you can mark the thread "solved" (it's a dropdown at "Thread Tools") which helps other people with a similar problem.

---

