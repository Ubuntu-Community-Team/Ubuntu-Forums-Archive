---
title: "Simple backup software?!?!?"
date: 2009-12-22
forum: General Help
---

### Post by besweeet on 2009-12-22
I cannot find ANY backup software that does what I want it to do. They're all basically the same and it's really pissing me off.

Why doesn't Ubuntu have a built-in backup program like Windows 7 and Mac OS X does? This is driving me insane!

All I want to do is backup everything that's installed, so that in the event of a failure, I can reinstall Ubuntu, restore the backup, and everything will be the way it was before the failure occurred. Is that too much to ask?

All the backup software that I've tried ask for me to 'include' and 'exclude' folders for the backup. I want it ALL to be backed up, not just certain folders.

Anyone? Anyone at all?

---

### Post by audiomick on 2009-12-22
I am about to try out this:
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
as a way of re-installing all the programs. I hope it works...:P

As far as your date and configuration (for evolution etc.) goes, that is all in /home. If you have that on a separate partition, you can just remount it during a new install (without formatting, of course). Otherwise, you'll have to back it up and play it back in after the new install.

---

### Post by Roasted on 2009-12-22
> **besweeet said:**
> I cannot find ANY backup software that does what I want it to do. They're all basically the same and it's really pissing me off.

Why doesn't Ubuntu have a built-in backup program like Windows 7 and Mac OS X does? This is driving me insane!

All I want to do is backup everything that's installed, so that in the event of a failure, I can reinstall Ubuntu, restore the backup, and everything will be the way it was before the failure occurred. Is that too much to ask?

All the backup software that I've tried ask for me to 'include' and 'exclude' folders for the backup. I want it ALL to be backed up, not just certain folders.

Anyone? Anyone at all?

I have yet to come across some sort of backup software that backs up your programs and everything, including on Windows 7, unless you make an actual image of your system, which you can do with a free and completely open source program known as Clonezilla LiveCD - which I do on all of my systems, regardless of the operating system.

In Ubuntu, Windows, whatever, I always use a program that automatically synchronizes all of my stuff in my documents folder, or in the case of Ubuntu, my home directory, to another drive on my system. In Windows I use SyncBack, on Ubuntu I use "rsync". That way every day at a certain time it'll back everything up. Sure, it doesn't back up my programs, but like I said - besides making an image, I don't know of anything else that will.

Speaking along those same lines, I also do monthly backup images of my root partition, which stores all of my programs and such. That way if my system tanks, I can barf out my backup image, bring my data over from my backup drive, and blam = I'm ready to go.

I do consider you look into those avenues. Clonezilla LiveCD is exceptional in terms of functionality and how easy it is to just click click click - bam, you're making a backup image. Weeeee!

---

### Post by Hallvor on 2009-12-22
> **besweeet said:**
> I cannot find ANY backup software that does what I want it to do. They're all basically the same and it's really pissing me off.

Why doesn't Ubuntu have a built-in backup program like Windows 7 and Mac OS X does? This is driving me insane!

All I want to do is backup everything that's installed, so that in the event of a failure, I can reinstall Ubuntu, restore the backup, and everything will be the way it was before the failure occurred. Is that too much to ask?

All the backup software that I've tried ask for me to 'include' and 'exclude' folders for the backup. I want it ALL to be backed up, not just certain folders.

Anyone? Anyone at all?

I use a livecd with partimage to clone the system partition. It is a bit crude but it never fails.

---

### Post by howefield on 2009-12-22
> **besweeet said:**
> and it's really pissing me off.

> This is driving me insane!

> Is that too much to ask?

> I want it ALL to be backed up

> Anyone? Anyone at all?

Calm down, you'll have some sort of seizure... as already mentioned, Clonezilla is your friend. Superb software.

---

### Post by egalvan on 2009-12-22
> **besweeet said:**
> 

All the backup software that I've tried ask for me to 'include' and 'exclude' folders for the backup. I want it ALL to be backed up, not just certain folders.

Anyone? Anyone at all?

When the software asks you which folders to backup,
tell it "ALL OF THEM".

Is that so hard? :)

---

### Post by asmoore82 on 2009-12-22
[SIZE="5"][COLOR="Blue"]+1 for Clonezilla[/COLOR][/SIZE]
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by houseworkshy on 2009-12-22
There is a program in the repositories called Aptoncd.  Backs up programs drivers folder whatever, the disc it produces can be used offline, very neat backup indeed.

---

### Post by houseworkshy on 2009-12-22
If you do install it the link to it will be made in System>Administration>APTonCD so you will need your password, as would anyone who got hold of one of your discs, which is also good.

---

### Post by besweeet on 2009-12-22
I'll give dd a try.

---

### Post by besweeet on 2009-12-22
Yup, did:
```
sudo dd if=/dev/sda3 of=/media/LinBackup/Image.img bs=4096 conv=notrunc,noerror
```

And it seemed to have done what I wanted it to do.

---

### Post by besweeet on 2010-01-27
Needed to reinstall (restore from a backup, actually) all my OSs due to a new hard drive. I was able to boot from the live CD to dd the image I made of my Ubuntu partition to the new one, and all the files seemed to have been copied. I just need to get GRUB2 installed.

If I try to boot the Ubuntu partition, it'll say GRUB.. and have a blinking cursor and won't actually do anything.

What do I need to do?

---

### Post by sourchier on 2010-06-12
You could try super grub to restore your grub booter.

The url is:

[http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")

This program will help you get your bootloader back.

---

