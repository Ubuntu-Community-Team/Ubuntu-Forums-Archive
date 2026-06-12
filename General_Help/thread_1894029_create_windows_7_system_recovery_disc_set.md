---
title: "create windows 7 system recovery disc set"
date: 2011-12-11
forum: General Help
---

### Post by goodbye-windows(tm) on 2011-12-11
Hi All,

I bought a (new) Dell 15r that will not allow me to create a set of system recovery disks. I haven't moved linux to it yet. 

Dell claims there is a partition with the system recovery data on it, but strongly suggests that a set of recovery DVD's be created, and then safely stored for future use if needed.

I have no experience with Windows 7, and this is my first 64 bit system.

But the utility program they give for creating the system recovery DVD set always fails on the second DVD, and always stops at 50 percent of the final (verification) step in the burning process.

Is there any way to use linux to save the factory installed system recovery partition? Conezilla would do the job, but I do not want to buy a 750 GB hard drive (my Dell has a 640 GB drive).

Appreciate any help.

Regards,

Art

---

### Post by dandnsmith on 2011-12-11
If it's indeed a new PC, then get on to Dell support, and tell them the DVD writer must be faulty, as it consistently fails to write the diks without a problem. They should then supply a new one, and may install it for you (depending on what type of support you have).

---

### Post by coffeecat on 2011-12-11
Another possibility is a corrupted file in the recovery partition. The verification process would probably be some sort of checksum, and it's significant that it's consistently the second DVD that fails. If the first passes, then it could be a file that belongs in the second DVD that is corrupted.

Explain the situation to Dell and hope that you get someone on the help desk who lives up to the name. At the very least they should supply you with a free set of recovery DVDs. At most they should re-install the OS and the recovery partition for you.

---

### Post by BC59 on 2011-12-11
You can apply online to Dell for Backup Disks:

[http://support.dell.com/support/topics/global.aspx/support/dellcare/en/backupcd_form?c=us&l=en&s=gen](http://support.dell.com/support/topics/global.aspx/support/dellcare/en/backupcd_form?c=us&l=en&s=gen)

---

### Post by Derek Karpinski on 2011-12-11
Are you using Maxell DVD's?  They always seem to fail.

I've personally never worried about the system recovery disks from the manufacturer.  The sys recovery and full win 7 install disk isos can be found online, and are completely valid. You will need your windows activation key though.  The amount of bloat and services that are set up to run with the manufacturers disks is amazing.  You can save yourself 5-10GB and 20-30 running processes by doing a clean install. Ninety percent of the time, the drivers will come in automatically when installing.

---

### Post by goodbye-windows(tm) on 2011-12-11
TY to all for the guidance. I'll contact Dell for support. This is my  second day that I've spent working on the problem, and I'm really  thinking it's time for Dell to feel some of my pain.

Bye the way, if anyone is considering buying a Dell, I'd definitely NOT  recommend it. The computer is overstuffed with third party software and  blatant advertising. It's very hard to spot the what's junk and what is  not. It will probably take me weeks just to get the Dell junk  exorcized!!! And, windows 7 is just as bad-I don't understand why people  put up with windows. 

Before the Dell was delivered, I had been windows/microsoft free for 3 months, and I am pretty proud of it! 

The best to all.....

Regards,

Art

---

### Post by goodbye-windows(tm) on 2011-12-11
Hi Derek,

I know about the maxell DVD's......I won't even allow them through the front door of the house.

It's not likely to be a problem with the discs themselves. I have attempted to create the recovery set twice, the first disc works fine. The second disk appears to be progressing nicely, but the progress stops in the last step of the writing procedure (verification) at exactly 50 percent. 

GL,

Art

---

### Post by Derek Karpinski on 2011-12-11
[http://www.mydigitallife.info/windows-7-iso-x86-and-x64-official-direct-download-links-ultimate-professional-and-home-premium/](http://www.mydigitallife.info/windows-7-iso-x86-and-x64-official-direct-download-links-ultimate-professional-and-home-premium/)

for Win7 isos.  These are not cracked versions, but genuine MS Win isos.

---

### Post by oldtimer7777 on 2011-12-11
What I suggest you do is order a set of silver pressed restoration dvds from Dell instead. They last longer just in case you need to switch back. Yes, they charge you a small fee to ship them out to you but that is it. 

> **goodbye-windows(tm) said:**
> Hi All,

I bought a (new) Dell 15r that will not allow me to create a set of system recovery disks. I haven't moved linux to it yet. 

Dell claims there is a partition with the system recovery data on it, but strongly suggests that a set of recovery DVD's be created, and then safely stored for future use if needed.

I have no experience with Windows 7, and this is my first 64 bit system.

But the utility program they give for creating the system recovery DVD set always fails on the second DVD, and always stops at 50 percent of the final (verification) step in the burning process.

Is there any way to use linux to save the factory installed system recovery partition? Conezilla would do the job, but I do not want to buy a 750 GB hard drive (my Dell has a 640 GB drive).

Appreciate any help.

Regards,

Art

---

### Post by Mark Phelps on 2011-12-12
Instead of going to all this trouble -- only to end up with a set of disks that will restore your PC to its original state, forcing you to lose all your data and apps, why not just image off Win7 to an external drive, or to DVDs?

You can download and install the free version of Macrium Reflect to do just that. That way, if you even need to restore Win7, you will get it with all the stuff already working, and not have to start over from scratch.

---

### Post by goodbye-windows(tm) on 2011-12-12
Dell tech support think the Memorex DVD's are the issue, I'll get some other brand and try again. Will post results when known.

Thanks for the info oldtimer.....I didn't even realize they made pressed CD's/DVD's these days!!!

Mark, I didn't realize there was another software option...other than clonezilla (which will only image the entire drive). I hope Macriam Reflect is open source. I am pretty serious about avoiding programs that aren't open sourced, especially on the Linux partition!!! Window 7 is there for the very rare times when I have to have window available....it's likely I will rarely use it.

Regards,

Art

---

### Post by coffeecat on 2011-12-12
> **goodbye-windows(tm) said:**
> I hope Macriam Reflect is open source. I am pretty serious about avoiding programs that aren't open sourced, especially on the Linux partition!!!

Macrium Reflect is definitely proprietary, not open source. But the free version is free as in beer and they don't hassle you to upgrade to the paid-for version. It is very good - I have used it myself. If it's any consolation to your open source sensibilities, the Macrium restore/repair CD that you create from the main app is Linux based! Which I find to be pleasantly ironic. :)

---

### Post by Mark Phelps on 2011-12-12
> **goodbye-windows(tm) said:**
> I hope Macriam Reflect is open source.

It's Macrium Reflect, and like nearly all Windows apps, it is not open-source.  But, the free version is not time-limited and comes with all the features needed to do backups and restores.

---

### Post by oldtimer7777 on 2011-12-12
> **Mark Phelps said:**
> It's Macrium Reflect, and like nearly all Windows apps, it is not open-source.  But, the free version is not time-limited and comes with all the features needed to do backups and restores.

I was coming from the point of view where this user may at some point wish to resell their computer to someone else, and -if- they do want to resell their computer, they probably need the factory restoration discs. You can easily order them from the manufacturers web site for a small fee, and then for now, you can rock out with your computer any way you want, and you don't have to worry about restoration partitions, or anything like that. If you don't want to resell it eventually, or you don't need that option to resell it later on, then use Macrium or Clonezilla instead. If I was going to buy a used computer, I would definitely wish to have those restoration discs no matter what, or I would find a used computer that did have them to purchase.

---

### Post by Mark Phelps on 2011-12-12
> **oldtimer7777 said:**
> I was coming from the point of view where this user may at some point wish to resell their computer to someone else ...

From that POV, you would DEFINITELY want to use the factory restore option -- if for no other reason, than to remove any personal settings or data.

However, if that only reformats the drive, you would still want to WIPE the drive first -- thus mandating that you had offline media for doing the factory restore.

---

