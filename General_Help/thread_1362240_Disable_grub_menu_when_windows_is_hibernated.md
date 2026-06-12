---
title: "Disable grub menu when windows is hibernated"
date: 2009-12-22
forum: General Help
---

### Post by rockofclay on 2009-12-22
Hi there,

Is there a way to disable grub and boot straight into windows when windows has been hibernated?

I am using karmic and windows xp (soon to become windows 7). I've recently done some damage by forgetting windows was still going, and I'm hoping I can stop it from happening again!

Cheers

---

### Post by dcstar on 2009-12-23
> **rockofclay said:**
> Hi there,

Is there a way to disable grub and boot straight into windows when windows has been hibernated?

I am using karmic and windows xp (soon to become windows 7). I've recently done some damage by forgetting windows was still going, and I'm hoping I can stop it from happening again!


Set Grub to boot into the last selection:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by rockofclay on 2009-12-23
Well, that helps a little, but not if I leave my computer off for a few days and forget I've hibernated.

Can grub be scripted?

I found [this]("http://www.inference.phy.cam.ac.uk/saw27/notes/detect-hibernated-windows-from-linux.html") which is a method of detecting a hibernated windows partition. I've no clue how to implement it in grub/ubuntu startup though. I imagine the NTFS partition would provide problems.

Perhaps a custom hibernate script could be set up in windows that saves a file in an accessible location.

I guess a read only lock on a hibernated NTFS drive would work also.

---

### Post by wilee-nilee on 2009-12-23
You can install startup manager from synaptic and set it to default to windows in grub2.

---

### Post by rockofclay on 2009-12-23
That doesn't help.

I want to either bypass the grub menu ONLY when windows has been hibernated, or loose write support to ntfs if I detect that the windows partition has been hibernated.

I don't want to be stuck using windows all of the time.

---

### Post by wilee-nilee on 2009-12-23
You wont be stuck with using windows all the time. What your looking for is a windows/Linux compatible script...good luck with that. Why don't you just shut-down the system your using, the hibernate start up takes as long as a regular start up and leaves you screwing it up if you forget.

The method I suggested is a insurance policy for when you forget the hibernate, but it seems apparent that since you can't remember how you shut your computer down or understand that the way your doing it is a waste of time there is no hope for you. ;)

---

### Post by rockofclay on 2009-12-23
> **wilee-nilee said:**
> You wont be stuck with using windows all the time. What your looking for is a windows/Linux compatible script...good luck with that. Why don't you just shut-down the system your using, the hibernate start up takes as long as a regular start up and leaves you screwing it up if you forget.

The method I suggested is a insurance policy for when you forget the hibernate, but it seems apparent that since you can't remember how you shut your computer down or understand that the way your doing it is a waste of time there is no hope for you. ;)


Look, there's no need to get angry. If you don't know how to help me, that's fine, but if I've already said no to the last boot option, why would I like your idea? Your method is not an insurance policy, as most of the time I'll prefer to boot ubuntu, and if I have forgotten that I've hibernated, I'll still do so.

I have shown that there is a script already to detect an in use hibernate file. That is a Windows/Linux compatible script already, but maybe you didn't read my posts. What I want to know is how to implement it in the grub boot menu, or when the drives are being mounted. I thought it may have been important for an operating system to protect against accidental miss use.

Occasionally I have to use hibernate when I'm in the middle of working on simulations, it can take a long time to shut down, so your assumption of wasted time is false.

---

### Post by Leppie on 2009-12-23
why don't you convert to ntfs? i'm using ntfs and when windows is hibernated i can boot ubuntu and after that boot into windows without any problems. also the link you provided confirms that this is only an issue with fat filesystems.

---

### Post by rockofclay on 2009-12-23
I am using NTFS.

The thing is I don't want to damage a partition by booting into ubuntu with full write support for the hibernated partition. It's dangerous, and I would like to avoid it.

The way I see this it could be achieved one of three ways.

1: Grub detects an active hiberfil.sys and decides to boot windows (This one is the ideal situation)

2: Ubuntu mounts the NTFS partition at read-only startup, checks for the active hiberfil.sys, if it is not active, it unmounts, and mounts again as read only. (This seems the most achievable).

3: Windows runs a script when it is about to hibernate that can makes grub boot resume it next time around. (Could be done with editing the grub menu, or by placing a flag that grub can read)

Can bash/any other scripting be set up with grub2? If so, can a NTFS drive be mounted this early on?

Where I could place a script that runs on startup with the privileges to mount NTFS drives? I could use this to force a read-only boot when windows is hibernated.

I wonder if it's possible to write a windows script that occurs on hibernate that changes grubs boot menu. Possibly a bit dodgy, this one seems the least likely

Oh, and the bash script for detecting an active hibernate is [here]("http://www.inference.phy.cam.ac.uk/saw27/notes/checkwin")

Any thoughts?

---

### Post by Leppie on 2009-12-23
i believe that as long as you don't touch the hiberfil.sys file on the windows partition, you should be ok (of course other system files should not be touched either).
i don't really see the issue here. as i stated before, i use hibernation as well and i can boot into ubuntu normally and use documents on the windows partition without damaging the system (i suppose as long as you don't modify the documents open in the saved windows session). if you know that you're not going to use windows for several days, i suppose shutting down is a better option than hibernating.

---

### Post by rockofclay on 2009-12-23
It's a dangerous practice.

The operating system leaves file handles open, programs may have cached writes etcetera.

I have already corrupted a directory because of this.

---

### Post by gjohny on 2010-04-12
I recently  run into problems after a windows hibernation, and haven't figured out to get out of it. My laptop is booting directly into linux 9.04,  no access to bios, or prompt screen for where to boot from. No special keys (F1, F2, F12, delect seem to help) is that a symptom?  

I like the way you are thinking about having grub check first.

---

