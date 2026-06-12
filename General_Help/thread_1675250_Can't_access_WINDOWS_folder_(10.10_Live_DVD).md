---
title: "Can't access WINDOWS folder (10.10 Live DVD)"
date: 2011-01-25
forum: General Help
---

### Post by kazakore on 2011-01-25
Hi all.

My laptop froze up this morning and required a forceful shutdown and since will not boot. it is a new drive in the machine and have to admit I had not tried my old Ubuntu partition since cloning the drive from my one I RMA'd to Western Digital.

So I have downloaded 10.10 Desktop version and burnt to a DVD.

If I try and use Nautilus I can not view anything on the WinXP partition but I can access my NTFS Data drive and my old Ubuntu Studio partitions (which I can't boot although I see Grub options.)

If I go via Terminal I can get at least some access though...

What Ubuntu is showing as the name looks suspiciously like a Windows serial number. Is it in fact what I registered my Windows with?

Once I get into the Win partition I can view contents of C's root. Here I can view the boot.ini file (which all help on the internet I could find claimed had probably got corrupted) but it looks as it should. I can get into Program File and Documents and Settings so some of the drive seems to work (and I should be able to back up my settings, all Docs and data already live on another partition anyway.) But it will not access the WINDOWS folder. This means I can not try replacing stated missing files from WINDOWS/system32.

Is this because either part of WINDOWS has become corrupt? Or the Address Headers for it? Or is there something that locks off Ubuntu from accessing this that I need to change? Seems strange I get nothing at all listed for the WinXP drive on Nautilus but at least some access with Terminal.

Is there a Check Disk type program within Ubuntu that can work on NTFS partitions? Last time I checked (fair few months ago now) there wasn't but here's hoping to progress...


Thanks for any help you can give :)

---

### Post by coffeecat on 2011-01-25
It certainly sounds as though your C: partition has suffered filesystem corruption, but how did you manage to mount it? Normally, Ubuntu will not mount a NTFS filesystem which is damaged so as  to prevent further damage.

Anyway...

> **kazakore said:**
> What Ubuntu is showing as the name looks suspiciously like a Windows serial number. Is it in fact what I registered my Windows with?

Where is this showing? What's the number? It could be the UUID. If the partition has no label then Ubuntu will mount it to a folder in /media named with the UUID.

> **kazakore said:**
> Is there a Check Disk type program within Ubuntu that can work on NTFS partitions? Last time I checked (fair few months ago now) there wasn't but here's hoping to progress...

No. The nearest is ntfsfix, but...

[quote="man ntfsfix"] ntfsfix  is a utility that fixes some common NTFS problems.  ntfsfix is NOT a Linux version of chkdsk.  It only repairs some  fundamental  NTFS inconsistencies,  resets  the  NTFS  journal file and schedules an NTFS consistency check for the first boot into Windows.[/quote]

Have you tried pressing F8 to get into safe mode? If that doesn't work you need to run chkdsk somehow. Can you borrow or get hold of a Microsoft XP install disc from which you could run chkdsk from the recovery console? Or do you have another machine with Windows and a USB enclosure for laptop drives? You could fit the drive into the enclosure, plug it into another Windows machine and run chkdsk from that.

Or you could use Hiren's Boot CD which (apparently) has a mini XP on it from which you can run chkdsk, but I have no experience of this. Links:

[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)

[http://www.hirensbootcd.org/download/](http://www.hirensbootcd.org/download/)

Last option that I can think of is: do you know anyone who has a Vista or Win7 install DVD? You can boot with that and drop to a command prompt from which you can run chkdsk. Or if you know of someone with a working Windows 7, you can create a repair DVD from that in which you can get a Windows command prompt and chkdsk. But I don't know how compatible the Vista/7 chkdsk is with an XP installation. It *should* be OK but I believe there was some further development to the NTFS flesystem in Vista/7.

---

### Post by kazakore on 2011-01-25
> **coffeecat said:**
> It certainly sounds as though your C: partition has suffered filesystem corruption, but how did you manage to mount it? Normally, Ubuntu will not mount a NTFS filesystem which is damaged so as  to prevent further damage.


If I open Nautilus it shows my three main partitions on the left, "31 GB Filesystem" ; "Data" and "39 GB Filesystem" These are WinXP, NTFS Data Storage, and old Ubuntu Studio installation respectively.

If I click on 31 GB Filesystem to try and get Nautilus to view contents it mounts it but shows nothing within it. I can then find it in Terminal by going to //media and listing contents. 

> Where is this showing? What's the number? It could be the UUID. If the partition has no label then Ubuntu will mount it to a folder in /media named with the UUID.

OK not Windows serial as only 16 character headecimal so probably the UUID. The Ubuntu Studio does also show with a very strange string when mounted and viewed in Terminal, but that's more likely to be to do with address of partition isn't it?



> No. The nearest is ntfsfix, but...

Don't think I'd risk that but good to know I was correct and thinking there still wasn't a product worth trying if you're worried.

> Have you tried pressing F8 to get into safe mode?

Doesn't get far enough to try that. When trying to boot get a black screen for ages and then told Hal.dll is missing. Seems Microsoft think it's either boot.ini corrupted or hardware failure. As boot.ini seems OK from within Ubuntu I'm thinking the later.
[http://support.microsoft.com/kb/314477](http://support.microsoft.com/kb/314477)

> If that doesn't work you need to run chkdsk somehow. Can you borrow or get hold of a Microsoft XP install disc from which you could run chkdsk from the recovery console? Or do you have another machine with Windows and a USB enclosure for laptop drives? You could fit the drive into the enclosure, plug it into another Windows machine and run chkdsk from that.

I will get hold of an XP disk was just hoping for a quicker way to work towards a solution today as our IT department do not have one which I can get to boot (and work mainly with network based installs anyway.) I had one of those multi-format USB caddies but not sure I still have it. All my externals us 3.5" drives.

> Or you could use Hiren's Boot CD which (apparently) has a mini XP on it from which you can run chkdsk, but I have no experience of this. Links:

[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)

[http://www.hirensbootcd.org/download/](http://www.hirensbootcd.org/download/)

Hadn't thought of Hiren's and didn't come up through my Googling so that's a possibility...

> Last option that I can think of is: do you know anyone who has a Vista or Win7 install DVD? You can boot with that and drop to a command prompt from which you can run chkdsk. Or if you know of someone with a working Windows 7, you can create a repair DVD from that in which you can get a Windows command prompt and chkdsk. But I don't know how compatible the Vista/7 chkdsk is with an XP installation. It *should* be OK but I believe there was some further development to the NTFS flesystem in Vista/7.

Think I'll try rather to get hold of an XP disk again, hopefully I can find mine when I'm home.



Trying to copy Documents&Settings over at the moment and getting a lot of Input/Output errors ("cannot stat" and "reading" ones) so think more than just main Windows drive may be damaged... :(

---

### Post by Tarnie on 2011-04-06
Hi, I'm just new in Ubuntu world and my English is not perfect. So let i explain what'i going on in my computer and maybe someone can help me please.
Two day ago I my windows just die, I tried few time to do a recovery but it doesn't work. So I download Ubuntu live for a Usb drive Pen  to try to recovery all my old pictures and documents for Windows.
I tried every thing, but it's no way to find my hard drive with all the file. if i go Places/computer just find the current file system from ubuntu and anything else.
I don' know what i can do right now, i just want to find my all old files before install definitely Ubuntu and just say good bye to windows seven.
I hope some one can help.

---

### Post by Dupointx on 2011-04-06
> **Tarnie said:**
> Hi, I'm just new in Ubuntu world and my English is not perfect. So let i explain what'i going on in my computer and maybe someone can help me please.
Two day ago I my windows just die, I tried few time to do a recovery but it doesn't work. So I download Ubuntu live for a Usb drive Pen  to try to recovery all my old pictures and documents for Windows.
I tried every thing, but it's no way to find my hard drive with all the file. if i go Places/computer just find the current file system from ubuntu and anything else.
I don' know what i can do right now, i just want to find my all old files before install definitely Ubuntu and just say good bye to windows seven.
I hope some one can help.

Please make a new thread and post your issue there.

---

