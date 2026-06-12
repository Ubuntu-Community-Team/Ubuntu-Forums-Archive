---
title: "A question on DD usage"
date: 2010-07-14
forum: General Help
---

### Post by alphaamanitin on 2010-07-14
Hello Ubuntu forum,

I have been building a computer for my girlfriend (sadly windows), and need to back up things from her old computer.  Here is the problem:

Her old computer has two IDE hard drive in it (one 80gb and one 250gb, I think), one running windows XP, the other is storage.  I want to back them both up-completely.  I was planning on installing a third 750gb HD in it booting from a live Ubuntu disc and using DD to copy the drives.  Here is my question-can I copy both drives to seperate partitions of the new 750gb hard drive?  Would it be easier to buy a new HD and copy each drive to a new HD?  

Also, anyone have a guess how long it will take to do this?  

Thanks Ubuntu Community

AlphaA

---

### Post by nmaster on 2010-07-14
dd will make an image of the drive.  you'll end up with two huge files.  this probably isn't what you want.  you should backup the data with something else (simply tarring it with bzip2 would be fine) and then just restore it onto the new drive.  

if you were looking to reuse the XP installation, that probably won't work since the new computer will have different hardware.

---

### Post by endotherm on 2010-07-14
i have to agree, a simple copy is often the best bet, as restoring from an image can be clumbsy. if you really want to image it, i would probably try partimage first before going to dd.

---

### Post by alphaamanitin on 2010-07-14
> **neal.m.master said:**
> dd will make an image of the drive.  you'll end up with two huge files.  this probably isn't what you want.  you should backup the data with something else (simply tarring it with bzip2 would be fine) and then just restore it onto the new drive.  

if you were looking to reuse the XP installation, that probably won't work since the new computer will have different hardware.


It was my understanding that a command like this: [COLOR=Red]dd if=/dev/sda of=/dev/sdb[/COLOR] will clone sda byte for byte to sdb; not make an image of it.  To make an image I thought you needed-[COLOR=Red]dd if=/dev/hda of=/image.img[/COLOR].  I am not looking into reusing the XP installation, I just want to have access to every file that is on the drive and I have been unsatisfied by simply copying and pasting the files I want to a new drive.  I know that linux treats partitions like drives, so sda and sda1 are actually partitions on the same drive.  So what I really need to know is if it is safe to partition my 750gb drive into two equal partitions and then use the clone function of dd to copy each seperate hard drive to a partition on the same drive.  

Thanks for the input guys,

AlphaA

---

### Post by K.J. on 2010-07-14
Bad news: This won't work the way you want it to because the partition map won't be set correctly.

Good news! Burn yourself a copy of the gparted live cd. It has a feature for partition copying/cloning that will take care of all the details for you.

---

### Post by nmaster on 2010-07-14
or an even better option: just backup the files you want and forget about this low-level cloning stuff.  there's quite a bit of risk that things won't work exactly how you want them too.  

if you're unsatisfied with a simple cp, try tar with bzip2.  

you could try this too.  i've used it with windows, but i've used it for linux and read a lot of good things about it in general.
[http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)

---

### Post by alphaamanitin on 2010-07-14
> **K.J. said:**
> Bad news: This won't work the way you want it to because the partition map won't be set correctly.

Good news! Burn yourself a copy of the gparted live cd. It has a feature for partition copying/cloning that will take care of all the details for you.


Would you please explain exactly what you mean by "the partition map won't be set correctly"?  Is this referring to how the computer finds information on a hard drive in relation to the the reference point on the actually discs in a hard drive?  

Thanks,

AlphaA

---

### Post by alphaamanitin on 2010-07-14
> **neal.m.master said:**
> or an even better option: just backup the files you want and forget about this low-level cloning stuff.  there's quite a bit of risk that things won't work exactly how you want them too.  

if you're unsatisfied with a simple cp, try tar with bzip2.  

you could try this too.  i've used it with windows, but i've used it for linux and read a lot of good things about it in general.
[http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)


One of the major reasons I want to clone instead of any cp is that I do not want to have to sit down with my girlfriend and find every file that she wants saved, and move them around so that they are all in one place.   I was hoping to just clone the damn thing a let her deal with the files later.

AlphaA

---

### Post by K.J. on 2010-07-14
> **alphaamanitin said:**
> Would you please explain exactly what you mean by "the partition map won't be set correctly"?  Is this referring to how the computer finds information on a hard drive in relation to the the reference point on the actually discs in a hard drive?  

Thanks,

AlphaA

I mean, you create two partitions that are different sizes than the partitions you are cloning. Without copying the partition table, it's not going to work. So basically you'd need two drives to do it this way.

Gparted will take care of all of that for you.

Also, I have to disagree with Neil. There's definitely more risk of loss with just doing a copy and paste than with a DD. If the DD ran without error and you can successfully access the cloned partition, you know you have all of the data.

---

### Post by endotherm on 2010-07-14
a byte for byte copy of a binary file, is by definition an image. it's not a copy of the datafiles themselves as seen by the filesystem, but an exact duplication of the underlying disk data structure.

also sda is a drive, sda1 is the first partition on the drive sda.

---

### Post by alphaamanitin on 2010-07-14
> **endotherm said:**
> a byte for byte copy of a binary file, is by definition an image. it's not a copy of the datafiles themselves as seen by the filesystem, but an exact duplication of the underlying disk data structure.

also sda is a drive, sda1 is the first partition on the drive sda.


I did not know that, but I just meant that dd does not have to give you one large file to restore from, it can clone a drive.  As for the sda stuff, then would sda2 be the second partition on the drive sda?  This is what my understanding was based on a article I read.  I am on a different computer or I would provide the link to it. 

To K.J.-

I also thought that this was the simplest and safest way of dealing with the file issue.  If it was not for the fact that the drives are IDE I would just hook them up to the new computer as slaves and not worry about anything.  Except I am afraid the drives may be failing.  I am not sure, just that the computer freezes lots and everything except the drives are about 1 year old.

AlphaA

---

### Post by aphatak on 2010-07-14
If you are going to use the new 750GB drive to boot from, what I should do is -
[LIST=1]
[*]Disconnect both the existing drives
[*]Put the new drive in, and install the operating system in it.
[*]Connect the old drives one by one as secondary drives, and copy whatever files you find you need from each.
[*]Disconnect the old drives and lock them away as back-up copies.
[/LIST]
That way, you would spend zero time backing the drives up, and just the time required to copy to 'restore' them.  In fact that was exactly what *I* did when I built a new computer for myself.

---

### Post by nmaster on 2010-07-14
> **alphaamanitin said:**
> I do not want to have to sit down with my woman and find every file that she wants saved

1. "my woman"?? its 2010 buddy.  you don't own her.

2. we never said you can't cp/tar/fsarchiver everything.  just copy it all!  its simple, its easy, and (best of all) you won't have to sit down and talk to "your woman"

---

### Post by alphaamanitin on 2010-07-14
[QUOTE=neal.m.master;9589423]1. "my woman"?? its 2010 buddy.  you don't own her.

You know nothing of our relationship and therefore do not to what we may use as pet names or terms of endearment.  Did it ever occur to you that I use the term with affection and she calls me "her man"?  Or did you just decide that the only possible way I could use the term was in ownership of her?  

My question has been answered, I cannot dd the separate drive into partition on one drive.

Thanks for all the advice and the responses.

AlphaA

---

### Post by nmaster on 2010-07-14
> **alphaamanitin said:**
> 

You know nothing of our relationship and therefore do not to what we may use as pet names or terms of endearment.  Did it ever occur to you that I use the term with affection and she calls me "her man"?  Or did you just decide that the only possible way I could use the term was in ownership of her?  


1. you're not talking to her here.  don't use a pet name with people who don't know about it.  it leads to misunderstanding (like this one)

2. even if she does call you "her man" it doesn't matter.  possessive pronouns imply ownership.

---

### Post by alphaamanitin on 2010-07-14
> **neal.m.master said:**
> 1. you're not talking to her here.  don't use a pet name with people who don't know about it.  it leads to misunderstanding (like this one)

2. even if she does call you "her man" it doesn't matter.  possessive pronouns imply ownership.

I am no t going to get in a debate about this on here and this will be my last post on the issue.  However, my relationship is none of your business in the first place and you are the one who made it an issue.  I hate to tell you but you do not have the right to be offended by how refer my girlfriend.  It did not lead to a misunderstanding, it led to you making the assumption that I am a possessive person that acts as if I own my girlfriend.  

AlphaA

---

### Post by nmaster on 2010-07-16
i agree that we don't want to get into a debate.  i wasn't really offended too much, but i did make it an issue for a reason.  you should be careful about the things you say here (or to anyone who you don't know personally).  it could be very offensive to others, and i just wanted to make that clear to you.  i know you're probably not a sexist jerk, but i don't know you personally and most people here don't know you personally either.  

that being said, i apologize for being judgmental.

take away point to anyone reading this: be careful what you say.  everyone has the right to be offended by sexism

---

