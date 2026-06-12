---
title: "live cd writing to xp partition?"
date: 2010-02-19
forum: General Help
---

### Post by Burfoot on 2010-02-19
I had occasion to boot Ubuntu livecd yesterday on a Dell machine with XP installed. 

I pressed the Escape key during boot to see what might be happening behind the Graphic ......  and got a rather upsetting surprise ..... 

... apparently Ubuntu was reading and writing to the XP partition ..... without any notification to me. 

I don't have the exact wording to hand, but what is said was that the XP install was 'dirty' and it was fixing it ....  fixed! 

I used a 9.10 CD. 

Is there any information out there that addresses this behaviour? 
Is there a way to boot the CD and prevent this from happening? 
Has this been widely reported? 

Let me make it clear ........ I do not expect or want ANY liveCD to write to ANY partition on ANY PC I might boot using that liveCD without my explicit permission/instruction. 

That this liveCD did write to a partition without asking or informing me is sufficient cause for me never to use such a liveCD again.

---

### Post by Xero Xenith on 2010-02-19
Did you mount the XP partition in Ubuntu? If you did, then that's pretty much par for the course. Mounting something means it gets recognised and used as a file system. No files have been deleted, or anything like that?

---

### Post by Digikid on 2010-02-19
Hi....who are you again?

*runs back to RR*

---

### Post by pricetech on 2010-02-19
You came here for information, or to complain ??  I'm not clear on that so I'm asking.

---

### Post by Digikid on 2010-02-19
> **pricetech said:**
> You came here for information, or to complain ??  I'm not clear on that so I'm asking.

That is enough of that.  he came HERE to hopefully get answers to a sensible concern.  Please respectfully help him if you can.  He is not complaining but I share his concern.

---

### Post by New2Ubunt on 2010-02-19
I'm not sure whether the original poster was looking for information, but I would certainly appreciate some.
 
He said this happened while he was booting from the Live CD, so how could he have mounted the NTFS drive?

---

### Post by snowpine on 2010-02-19
You can do **anything** with a Live CD, up to and including completely reformatting your hard drive. It is a powerful tool.

---

### Post by New2Ubunt on 2010-02-19
> **snowpine said:**
> You can do **anything** with a Live CD, up to and including completely reformatting your hard drive. It is a powerful tool.
That's not in question.
 
The OP said this happened while he was booting from the live CD.

---

### Post by snowpine on 2010-02-19
The Ubuntu Live CD scans the internal drives during boot. (Among other things, it will automatically mount an existing swap partition.) This is a "feature not a bug." Your assumption that Ubuntu will not touch your HD is incorrect.

Since this is your first post on Ubuntuforums, you haven't provided any specific output messages, and as far as I know, your Windows install is undamaged, I will assume you are just asking for clarification on this point. "Should not access the computer's HD" is not a design goal for the Ubuntu Live CD.

---

### Post by theozzlives on 2010-02-19
> **Burfoot said:**
> I had occasion to boot Ubuntu livecd yesterday on a Dell machine with XP installed. 

I pressed the Escape key during boot to see what might be happening behind the Graphic ......  and got a rather upsetting surprise ..... 

... apparently Ubuntu was reading and writing to the XP partition ..... without any notification to me. 

I don't have the exact wording to hand, but what is said was that the XP install was 'dirty' and it was fixing it ....  fixed! 

I used a 9.10 CD. 

Is there any information out there that addresses this behaviour? 
Is there a way to boot the CD and prevent this from happening? 
Has this been widely reported? 

Let me make it clear ........ I do not expect or want ANY liveCD to write to ANY partition on ANY PC I might boot using that liveCD without my explicit permission/instruction. 

That this liveCD did write to a partition without asking or informing me is sufficient cause for me never to use such a liveCD again.

I don't know what happened, but I've never got rid of the xsplash by hitting esc, and I've never had an Ubuntu Live CD write or damage my existing filesystem without my permission. That's what boot without changes means. This is not a widespread incedent, as I fequent the forums daily and have never seen a post such as this. My guess is you got a Windows critter that made it's way to the CD kinda like Michaelangelo with floppies and DOS.

---

### Post by New2Ubunt on 2010-02-19
I'm getting very confused here.
 
Some of the replies are saying that the Live CD can change the host computer's filesystem while booting, and that it's OK, others are saying that it's impossible, and that if it happened, you would expect others to have posted about it.
 
So is it impossible, or is it by design? I would really like to know.

---

### Post by snowpine on 2010-02-19
> **New2Ubunt said:**
> I'm getting very confused here.
 
Some of the replies are saying that the Live CD can change the host computer's filesystem while booting, and that it's OK, others are saying that it's impossible, and that if it happened, you would expect others to have posted about it.
 
So is it impossible, or is it by design? I would really like to know.

Simply booting an Ubuntu Live CD should not damage your existing system. We are waiting to hear back from the original poster with more details of the "incident". (I am not convinced there is an actual problem here.)

The statement "an Ubuntu Live CD will completely ignore my hard drive" is incorrect. Your drive is scanned during the boot process, by design.

---

### Post by theozzlives on 2010-02-19
> **snowpine said:**
> Simply booting an Ubuntu Live CD should not damage your existing system. We are waiting to hear back from the original poster with more details of the "incident". (I am not convinced there is an actual problem here.)

The statement "an Ubuntu Live CD will completely ignore my hard drive" is incorrect. Your drive is scanned during the boot process, by design.

I disagree. You can boot a live CD without a hard drive.

---

### Post by snowpine on 2010-02-19
The first time I became aware of this "issue" was attempting to repartition my hard drive. Turns out the Ubuntu CD had automatically mounted my swap partition, preventing changes to the extended partition. "Why did it do that?!?" I remember asking. 

> **theozzlives said:**
> You can boot a live CD without a hard drive.

I agree.

---

### Post by theozzlives on 2010-02-19
> **snowpine said:**
> The first time I became aware of this "issue" was attempting to repartition my hard drive. Turns out the Ubuntu CD had automatically mounted my swap partition, preventing changes to the extended partition. "Why did it do that?!?" I remember asking.

Linux Distros will mount an existing Linux swap partition if there's insufficient memory to run the live CD. Fedora has been known to create one. Knoppix and DSL are known to create folders on your hard drive in an effort to create persistence.

---

### Post by New2Ubunt on 2010-02-19
It's clear enough that the Live CD has to scan any attached HDDs, otherwise it couldn't make a list of partitions which are available to mount.
 
It doesn't seem like a massive problem if it makes use of an existing Linux swap partition, even if it can be inconvenient, as noted above.
 
But if the Live CD, or even the installed O/S, can amend or 'fix' an NTFS partition which the user has not mounted, that could represent a serious problem - if I have a problem partition, I want to decide for myself what to do about it. Even Windows allows you to cancel a ChkDsk on startup.

---

### Post by Burfoot on 2010-02-19
I booted the CD .....  chose English ........ the first option .... boot without making any changes etc was highlighted ........ I hit return and waited a short time ....... the Ubuntu icon appeared in the middle of the screen ...... I hit escape and got a blank black screen ..... a short time later the following appeared on the screen .. 
"shadow passwords are now on" and after that various lines appeared as it booted. 
That was a couple of minutes ago .... and the Win XP partition was not in a 'dirty' state as it was when I saw the lines to the effect that Ubuntu had 'fixed' the problem. 

So contrary to the person who posted that hitting the Esc key does nothing for him, I can assure you I can get the info as described. 

Other lines such as 

Generating locales .... enUS-UTF-8 ...  done 
Generation complete 
Using CDROM mount point /cdrom/ 
identifying ...... <big long list of numbers & letters> 
Scanning disk for index files 
. and so on .... 

appeared under the password one. 

So does anyone know what these Shadow Passwords are? I have no idea. Might be something to do with Ubuntu. 

I feel confident that if I 'dirty' the XP install .....  maybe by unplugging the power while it is running ..... that the original event could be repeated. Presently I would prefer someone else to confirm that this is possible on their machine rather than to just repeat it on this machine. 

Last clarification .......  Ubuntu did NOT damage the XP installation. Rather it fixed it as it said it did. 
My only point is that I did not explicitly allow Ubuntu write to any partition in the PC, yet it did. 
In fact I chose the option that explicitly told me no changes would be made to any of my HDDs.

---

### Post by anim-eh on 2010-02-20
as i said on RR...most times i have used the live cd without actually making changes to my hard drive...if grub is not installed to the MBR, the ubuntu live cd will generally fix issues that correspond to the MigrationTools application...this is just my experience though

---

### Post by pricetech on 2010-02-22
> **Digikid said:**
> That is enough of that.  he came HERE to hopefully get answers to a sensible concern.  Please respectfully help him if you can.  He is not complaining but I share his concern.

Actually it was a legitimate question.  Frankly I'm still not certain.  Perhaps both.

Nonetheless if you are offended by my post, feel free to report it.

---

### Post by Digikid on 2010-02-28
Well next time word it a little more appropriately then so that it does not come off as snotty like before please.

Burfoot did you get your answer?

---

### Post by Mark Phelps on 2010-02-28
When the LiveCD boots, it creates a RAM drive because it needs to write some files to boot an OS.  It also scans all attached drives (if any) so it can build a drive list to be used in future operations.  Of course it can be used without a hard drive, but if one is there, and if there is a swap partition, it will scan the drive and use the swap partition.

In keeping with the displayed text -- that is NOT making changes to the hard drive.

As to the original post, if someone has a question, they should ASK IT -- not rant on about things they don't understand.

---

