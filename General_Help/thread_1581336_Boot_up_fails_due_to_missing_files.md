---
title: "Boot up fails due to missing files"
date: 2010-09-24
forum: General Help
---

### Post by mashroom on 2010-09-24
I installed 10.04 Lucid Lynx about a week ago, with GRUB so I could dual boot, and today when I booted into Ubuntu I was greeted with this screen: [IMG]http://sphotos.ak.fbcdn.net/hphotos-ak-snc4/hs677.snc4/61713_1617671127350_1403537932_1649005_1923619_n.jpg[/IMG]

I'm thinking of just rm -rfing the entire drive through recovery mode and reinstalling, but I want to know what's happening before I format it.

I had not installed and random packages, I'm pretty sure the only things I had installed were Wine 1.2 and swfdeck.

---

### Post by JedMeister on 2010-09-24
Obviously need more info. A pic or the exact words of the error would be helpful (I know you said you're off to get a pic, so that'll do it). 

In my experience with boot errors with Ubuntu, doing a google search with the exact error is often very useful for finding a fix.

Without knowing for sure I suspect that your boot is stalling in GRUB. GRUB (both legacy & 2) have a basic commandline where you may be able to get your system to boot. Personally I rather just boot with a live CD and fix from there. The beauty of that is that (assuming your network is supported) you can find the fix online and do it straight away using cut & paste (rather than having to find the fix, write stuff down or print it out etc).

Did you do any updates? Like a kernel update?

Whilst a clean install will solve your problem, chances are high that it may happen again (obviously depends on the cause).

[edit] Oops just realised you posted a pic while I was writing!

---

### Post by JedMeister on 2010-09-24
It looks like its not finding your filesystem. That's not one I've run across before and I'd still suggest writing down the exact error message and doing a google of it. 

I'm certainly no expert on these things (I consider myself a bit of a Linux newb still) but assuming you haven't done any updates to major packages recently or anything to your filesystem, I'd be checking for hardware issues (condition of HDD, cabling, PSU, etc).

Perhaps try booting with a LiveCD and running some disk diagnostics and checking that everything is actually there (see if its a HDD prob or an issue with GRUB getting lost). Assuming its a clean install of 10.04 (with GRUB2) its perhaps worth a try to mount the HDD (from the live CD) and 'update-grub' and see if it runs ok or errors (a quick search of the forums should find the relevant info on how to do that).

---

### Post by mashroom on 2010-09-24
The thing is, GRUB is booting Windows fine, so unless I'm totally reading your post wrong or I still don't know much about Linux, it's probably not GRUB getting lost.

---

### Post by JedMeister on 2010-09-24
> **mashroom said:**
> The thing is, GRUB is booting Windows fine, so unless I'm totally reading your post wrong or I still don't know much about Linux, it's probably not GRUB getting lost.Well if GRUB is booting Windows fine then at least that makes the likehood of it being a HDD failure a lot less.

I meant that GRUB is getting lost, in the sense that it is obviously not finding the files it needs to boot Ubuntu. Like I said above I'd try booting with a LiveCD and see whats going on with your Ubuntu partition. First I'd check that the files are actually there then assuming they are, try updating GRUB and see if it throws an error. Hopefully you can still get online when booted with a LiveCD, cause that makes it heaps easier, eg you can search online how to do things and follow instructions without having to write everything down.

---

### Post by mashroom on 2010-09-24
It's not booting up in the live CD at all, and now recovery mode isn't working at all.
So I guess rm -rf on the partition is the only way to go - but I can't even type in that white on black screen that comes up even though it seems like I should be able to.
 
:-({|=
 
EDIT!:
 
Nevermind, I'm dumb, I forgot you needed to press a key!
 
EDIT THE SECOND:
It's taking forever to boot up in CD!

---

### Post by mashroom on 2010-09-24
Half..
an..
hour..
 
AND IT'S NOT BOOTING OFF OF THE CD!
 
How do I rm -rf the Ubuntu partition without booting into it?

---

### Post by JedMeister on 2010-09-24
Not sure why your LiveCD is booting so slow, but anyway I just did a quick google and it seems like this problem is not uncommon. Usually this issue seems to be associated with laptop users whose laptops have not shutdown cleanly which has in turn damaged the filesystem leading to GRUB being unable to mount the filesystem. It has also been linked to failing hard drives. You may be able to fix it, but it seems many have needed to reformat and start again.

Have a read through these threads and see if any of it makes sense or is of use to you. Some relate to other versions of Ubuntu but for the purpose of this issue it probably shouldn't matter.
[http://ubuntuforums.org/showthread.php?t=1437015](http://ubuntuforums.org/showthread.php?t=1437015)
[http://ubuntuforums.org/showthread.php?t=1568704](http://ubuntuforums.org/showthread.php?t=1568704)
[http://ubuntuforums.org/showthread.php?t=1244466](http://ubuntuforums.org/showthread.php?t=1244466)

I've said I'm no expert but if there is anything there that you don't get, try posting back here and I'll help you as much as I can.

---

### Post by mashroom on 2010-09-24
On the third thread, it said something about testdisk. What is that?

---

### Post by JedMeister on 2010-09-24
Its a worry if your computer is not booting from LiveCD. Is that the CD you installed from? Double check its not damaged (scratched etc). Assuming it is the CD you installed from  and if you still have the ISO (and a spare blank CD) maybe try burning it again. Personally I usually install from a LiveCD so even if you want to try a clean install its going to be tricky. I guess your only other option is to either try creating a Live USB or try Wubi (my least favourite option). If the LiveCD worked previously, isn't damaged but doesn't work now, then perhaps it is hardware on the way out?

[Testdisk]("http://en.wikipedia.org/wiki/TestDisk") is for recovering data from a damaged HDD.

---

### Post by bcbc on 2010-09-24
before you wipe everything, try booting an older kernel, assuming you have more than one kernel

There've been some issues with 2.6.32-24 dropping to a busybox shell. Here's a thread with more info if this matches your prob [http://ubuntuforums.org/showthread.php?t=1565714](http://ubuntuforums.org/showthread.php?t=1565714)

---

### Post by mashroom on 2010-09-25
> **JedMeister said:**
> Its a worry if your computer is not booting from LiveCD. Is that the CD you installed from? Double check its not damaged (scratched etc). Assuming it is the CD you installed from and if you still have the ISO (and a spare blank CD) maybe try burning it again. Personally I usually install from a LiveCD so even if you want to try a clean install its going to be tricky. I guess your only other option is to either try creating a Live USB or try Wubi (my least favourite option). If the LiveCD worked previously, isn't damaged but doesn't work now, then perhaps it is hardware on the way out?
 
[Testdisk]("http://en.wikipedia.org/wiki/TestDisk") is for recovering data from a damaged HDD.
 
 
It is the CD I installed from, kept safe in a paper folder, and when I checked the disk surface, only one very small scratch. Using PartedMagic to reformat the partition, when I even try to VIEW the partition, it kept hanging.
 
HDD corruption? I think so.

---

### Post by CharlesA on 2010-09-25
Try this:

Boot off the Ubuntu CD and hit any key when the purple loading screen first comes out. Select "check disk for defects" and see if it passes.

Have you tried running fsck from a livecd?

---

### Post by mashroom on 2010-09-25
No, I haven't. I'll go see what I can do.
 
EDIT: It seems I lost the original CD, so I'm burning a new one. We'll see how that goes tomorrow - it's getting kinda late in my part of the world and I've been trying to fix this for a while now.

---

### Post by JBAlaska on 2010-09-25
When you get back...Is this by chance a wubi install (Did you install Ubuntu from inside windows)?

I remember seeing the error: > target filesystem doesn't have /sbin/init on a wubi install I had that went south.

If so [This](https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?) may help.

---

### Post by mashroom on 2010-09-25
> **JBAlaska said:**
> When you get back...Is this by chance a wubi install (Did you install Ubuntu from inside windows)?
 
I remember seeing the error: on a wubi install I had that went south.
 
If so [This]("https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?") may help.
 
No, it's not a wubi. I've heard that it's more unstable than a normal install.. so I went with a CD. Thanks for trying to help, though.

---

### Post by mashroom on 2010-09-26
*YES!!! *I got Ubuntu back up and running after formatting the partition and reinstalling. Definitely makes me mad that I have to set up users n junk all over again... but at least I don't have 30 gbs of dead weight sitting on my computer anymore.

---

### Post by JedMeister on 2010-09-26
Glad you got it sorted. But still not good it happened in the first place! I'd be inclined to make sure you back up everything important on that HDD from here on in (not that you shouldn't always backup important stuff, but especially now).

Hope it keeps going ok for you.

---

