---
title: "Ubuntu 9.04 clobbered, most apps now missing"
date: 2010-09-22
forum: General Help
---

### Post by oygle on 2010-09-22
I was having problems with using sound in 9.04, and decided that I needed to upgrade to 10.04

So, did a bit of cleaning up, before doing a backup to another disk. In the process of cleaning up, I removed, what I thought was "just" sqlite, but it removed firefox, kmail, nautilus, networking, internet, just about all menus, the whole system is shot.

Fortunately, I use simple backup, and was able to 'see' that a full backup was done yesterday, and an incremental just before my 'clean up'.  The sbackup only does /home , and system data held in /etc,/usr/local and /var , so not ALL of the system is in the tar files.

Now when I boot into Ubuntu, it just goes to a command prompt. To copy those .tar files to another drive on the same computer, I need to run nautilus or similar, but can't, as no internet. The same with sbackup, basically it won't run anything. I did try the 'recovery option in GRUB, still no go.

I do have Beyond compare on the Ubuntu box, and I _think_ it may be ok to run, and possibly copy those .tar files across. As it won't even do a 'mount' either, I can't copy to CD, or load a USB stick, etc, etc.

I'm 99% certain that the .TAR files will be all that I need. They have all the data, and all the config. type files.

Just wondering if there is any method to get Ubuntu 9.04 up and going again, like a restore point I guess. But, every time I tried using apt-get, it wanted the internet, which is not working on Ubuntu (fortunately I have XP on this same computer, and can connect).

The XP computer can't access the Ubuntu HDD, but Ubuntu can access the XP HDD, and copy to it, but ONLY if I can mount the XP drive first.

So, I guess even if I could do a mount of that XP HDD from Ubuntu, that will be a start.

Oygle

---

### Post by SaintDanBert on 2010-09-22
There are limited undo and revert features within **deb** package management tools but they depend on how you did the original deed(s) and what else you may have done since the deed(s) was done.

I've managed a lot of systems over the years, and (grin) have a good collection of boots with bullet holes. Since you have good backup data and want to change to a new distro edition, I suggest:

[list=1]
[*]**Fresh Install** your new edition Lucid (v10.04 LTS)
[*]**Add Applications** dealing with differences between Jaunty (v9.04) and Lucid (v10.04 LTS) and filling with your favorites that are not installed by default. 
[*]**Restore** your data files
[*][color=orange]Learn to use undo and revert features of package tools.[/color] (grin)
[/list]

If you must have Jaunty back, I'd follow the same approach and **Fresh Install** Jaunty, Add apps, etc. Is it possible to recover from an over aggressive package removal, yes. I suspect that you will spend more time chasing dependency issues than you would to move files and configuration details from your backup data onto a fresh image.

Good luck,
~~~ 0;-Dan

---

### Post by oygle on 2010-09-22
Hi Dan,

Thanks for your reply, very helpful. I assume you are suggesting that I install 10.04 with the 'current 9.04 partition intact'. That is, do the 10.04 install, it recognises a Ubuntu partition, asks me what to do, I say 'leave the 9.04 there' for now.

It would be great if I could somehow do a mount manually, just to get those .TAR files on another computer, as I'm 99% sure Beyond Compare will run, as it uses its own libraries, and I think, therefore it has no dependencies that I may have removed.

I was able to do the mount command still, I guess I should try ..

```
sudo mount /media/disk
```

first, and see if that HDD is mounted. If it does, then I can use BC to push all of 9.04 to a seperate drive, and then when 10.04 is installed, I can (safely, hopefully) just format all other current partitions, and start afresh.

Thanks,

Oygle

---

### Post by SaintDanBert on 2010-09-23
No,I would wipe an install fresh and clean.  If there are details you need from Jaunty, you have your backup archives, but I wasn't thinking about a disk large enough for both distro editions.

Where your tar-balls are concerned, launch a live-CD -- you'll have one for either Jaunty or Lucid, right? I'd then connect an external drive, mount your other file systems and copy to  your heart's contentment.
The live-CD approach leaves your HDD unscathed until you harvest whatever your want. I'd strongly consider running **fsck** over your file systems before you create your tar-balls. This is specifically true if you plan to create a fresh archive 
```

tar {options} -cvf everything.tar.gz /*

```

If you are going to discard Jaunty anyway, you are mostly interested in content rather than organization. That said, if you have a large enough external drive, **cp -av** or **rsync -a** to save the content.
Once you complete the fresh install, paw through the copy for things to keep. At $80 USD for a terabyte, it might be worth the trip to a byte store.

Over my career, I've wasted too many hours "... I ought to be able to fix my mistake ..." rather than remember my original mission and working to get from whatever mess I have to where I want to be soonest and easiest.

Cheers,
~~~ 0;-Dan

---

### Post by HermanAB on 2010-09-23
Backup your data and re-install - seriously.  Trying to fix a mess like that is not worth the time and effort.  Next time make a separate /home partition, then you can re-install or upgrade without wiping your data - just don't format /home during the install.

---

### Post by oygle on 2010-09-23
Hi Dan,

> **SaintDanBert said:**
> If there are details you need from Jaunty, you have your backup archives

Yes, all my data is on the backup archives. Well, 99% of it anyway.

> **SaintDanBert said:**
> Where your tar-balls are concerned, launch a live-CD -- ...I'd then connect an external drive, mount your other file systems and copy to  your heart's contentment.

I only had a 9.04 alternate CD, and it wouldn't boot. But I did have an i386 10.04 desktop, it booted fine, and I was able to access the tar-balls and copy them to another HDD on the same computer. However, trying to navigate with the CD booted, and 2 HDD's, it was painful, as I got constantly stuck on permissions, and couldn't run this or that. Although the tar-balls were copied, there are indeed other files to retrieve from the clobbered 9.04 HDD, and I have no easy way to ensure what was copied is exactly the same as the original tar-ball.


> **SaintDanBert said:**
> I'd strongly consider running **fsck** over your file systems before you create your tar-balls. This is specifically true if you plan to create a fresh archive 
```

tar {options} -cvf everything.tar.gz /*

```

Fortunately, the 9.04 ran fsck by default, and all was well. But I think what you are saying, is to run fsck before the 'simple backup' is run automatically.

> **SaintDanBert said:**
> That said, if you have a large enough external drive, **cp -av** or **rsync -a** to save the content.

Okay, so one major consideration was for me to check data consistency between copying the tar-balls or any file/s. I was relying on Beyond Compare, as it is a great tool and runs on Debian, and does binary compares and all sorts of things. In the absence of being able to run BC, will the 'cp' or the 'rsync' compare the CRC or do a checksum or similar, to ensure data consistency when copying ?

Hi Herman,

> **HermanAB said:**
> Backup your data and re-install - seriously.  Trying to fix a mess like that is not worth the time and effort.  Next time make a separate /home partition, then you can re-install or upgrade without wiping your data - just don't format /home during the install.

The data is backed up okay, but is on the 'clobbered' 9.04 HDD. Well, at least 99% of the data I'd say. There are other files to sort through and grab. It's getting the data off to another HDD, and ensuring the data has been copied okay, that is a concern.

I think after the (minor) permission probs, and other issues with getting the data, and the consideration to go to 10.04 anyway, might be best to do this ...

(this is current setup ..)

Computer A - Primary HDD Ubuntu 9.04 that is 'clobbered'
           - Secondary HDD has Win XP Pro

Computer B - Primary HDD Ubuntu 10.04 64 bit (no data)

Place the primary drive from Computer A in Computer B, as secondary, add all the apps to Comp B, then piece through the tar-balls and other stuff, and slowly rebuild all the data to the 64 bit 10.04 HDD.

That was the 'final' plan anyway, for sometime down the track. I was using Comp A to convert a lot of files, and sort through data files as general housekeeping.

Fortunately, Comp B is 'bare bones', no apps, so I can start afresh with that. From memory, I think I may have already set that up with a seperate /home partition.

Thanks to you both for your help,

Oygle

---

### Post by SaintDanBert on 2010-09-24
> **oygle said:**
> 
...
The data is backed up okay, but is on the 'clobbered' 9.04 HDD. Well, at least 99% of the data I'd say. There are other files to sort through and grab. It's getting the data off to another HDD, and ensuring the data has been copied okay, that is a concern.
...


In the future, consider a "cron job" or "udev rules" (or both) that will migrate your backup files from the running system to external storage on a periodic and routine basis.  You could also simply make an external copy if you need routine access to the backup files.  Regardless of implementation, demand connection of the external drive, migrate or copy the files, demand disconnect of the external drive.

In my paranoia, I might also consider a monthly job that would clone the external drive to intra-net (your server) or internet "cloud" storage. Now you have three layers of protection: (a) your back files, (b) the external drive copy, (c) the cloud copy.

Glad you are working. Hoping your foot feels better soon,
~~~ 0;-Dan

---

### Post by oygle on 2010-09-24
Hi Dan

> **SaintDanBert said:**
> In the future, consider a "cron job" or "udev rules" (or both) that will migrate your backup files from the running system to external storage on a periodic and routine basis.

Although I use sbackup to do automatted backups, I have found it may be a little bit inadequate, although it does a full every few days, and incremental each day. It would be 'nice' to have a full/complete copy of everything on an external drive. Have had some issues with [Mounting an external drive]("http://ubuntuforums.org/showthread.php?t=1580865"), but now they seem to be sorted out.

Simple backup uses tar I think. Would 'rsync' be better, I have never used it, but it seems it just copies new and changed files from source to destination.

> **SaintDanBert said:**
> In my paranoia, I might also consider a monthly job that would clone the external drive to intra-net (your server) or internet "cloud" storage. Now you have three layers of protection: (a) your back files, (b) the external drive copy, (c) the cloud copy.

The intra-net clone would be good; I only have broadband wireless with limited quota per mth (5 Gb), so I woudn't be able to upload any large files to an internet "cloud" storage.

Thanks for your help,

Oygle

---

### Post by SaintDanBert on 2010-09-25
> **oygle said:**
> 
...
Simple backup uses tar I think. Would 'rsync' be better, I have never used it, but it seems it just copies new and changed files from source to destination.


I use **LuckyBackup** [http://www.linux.com/component/content/article/322632?format=pdf](http://www.linux.com/component/content/article/322632?format=pdf)  It is a wrapper front end to **rsync**.  I used tar or cpio or **cp -av** for years. Since rsync will help manage the "save what changed" issue, it made lots of sense.  Cheap external storage and rsync makes it trivial to implement
"keep THAT SPACE identical with THIS SPACE."  I'll then use tar to snapshot the external drive and move it to my cloud space.

> **oygle said:**
> 
The intra-net clone would be good; I only have broadband wireless with limited quota per mth (5 Gb), so I woudn't be able to upload any large files to an internet "cloud" storage.


Several folks sell out-of-box network-based storage. If you have an olde pizza box, and USB drives ... (grin).  I'm going to set this up in  my home.  I'll use three 1 TB usb drives -- "yesterday" "today" "tomorrow" in rotation. Then once each month (or something) I'll take one drive off site.

In a prior life, I managed a mainframe with tape backup. We made a weekly "full save" followed by daily "what changed" saves. Every fifth week (average four weeks per month) we took the full save off site.
We cloned the end-of-December full save as a "year end". In those days, huge drives were 512 MB.  Tapes were 6250 bits-per-inch holding 40 MB per reel. I can only imagine (sweat, fear, loathing) backup of a multi-terabyte farm to (gulp) tapes.

Cheers,
~~~ 0;-Dan

---

### Post by oygle on 2010-09-25
> **SaintDanBert said:**
> I use **LuckyBackup** [http://www.linux.com/component/content/article/322632?format=pdf](http://www.linux.com/component/content/article/322632?format=pdf)  It is a wrapper front end to **rsync**.

Sounds better than simple backup, if it can use rsync. Seems it will keep a 'mirror' of all the file system, which would be great. Full backups with simple backup are over 10Gb, so it takes a fair slice of disk space, every few days.

> **SaintDanBert said:**
> 
Several folks sell out-of-box network-based storage. If you have an olde pizza box, and USB drives ... (grin).

Not too sure what is termed an olde pizza box. As all the data is now being shifted to a computer that has more grunt and disk space, there will be a possible 'slice of pizza', it has 2 Gb ram and a P4 3.0 Ghz CPU. The disk is only 200Gb, and it has 3 sectors that are failing, so considering that HDD would be 5 to 6 yrs old, it's time to toss it out. As you say, disk drives are fairly cheap; seems externals are cheaper than internals now, or maybe I have it wrong ?

Yes, I have always _tried_ to use the 'son/father'grandfather' cycle for backups; something I learnt in the old days from a tape system.

> **SaintDanBert said:**
> In a prior life, I managed a mainframe with tape backup. We made a weekly "full save" followed by daily "what changed" saves. Every fifth week (average four weeks per month) we took the full save off site.

Reminds me of my prior life. We had what were called 'minis', a step down from mainframes. All a tape system, and paper tape and punched cards. We operated it by using octal code to instruct the Honeywell computers. Tapes were stored off site every day, that is, the most recent 'master' copies. I can remember the engineers delivering 32K of memory, it took 2 of them to carry it in. Things sure have changed.  :D

Oygle

---

### Post by SaintDanBert on 2010-09-25
I use "pizza box" to refer to the old desktop computer form factor.  I'm sorry my use of jargon or slang was not meaningful.

I've worked with IBM 1410, 360, and 370, Burroughs 5500, CDC-6000, RCA-something, and then I discovered Digital (DEC) systems.  Starting with PDP-8 and PDP-11, then DecSystem-10 and later -20, then VAX/VMS and finally Alpha. I even worked with their Rainbow(tm) desktop computer.

Good times, glad to be FROM them,
~~~ 0;-Dan

---

### Post by oygle on 2010-09-26
Wow, seems we have had a fairly similar background, in terms of machines worked with/on. DEC/Digital's alpha was a nice little box, very powerful. I think the vax/vms rdms was designed around the same 'structure' as Interbase, as I had opportunity to use IB when Delphi, etc was the flavour.

Oh, .. I get it now, pizza box, yes those 'IBM' type computers, .. I'm a bit slow.  :)

---

### Post by SaintDanBert on 2010-09-28
> **oygle said:**
> ...

Oh, .. I get it now, pizza box, yes those 'IBM' type computers, .. I'm a bit slow.  :)


(laughing) We used to say that "{name}'s WAIT light was stuck on."

I really enjoyed my DEC years and the systems and software available.
Not only was official documentation plentiful, but it was also extremely readable. The community was also very active in supporting each other. The technology of the day meant "monthly newsletters" and similar instead of email or web pages, but odds were you could find an answer somewhere. We were doing things with our DEC systems that are only recently available on the "desktop" -- clusters, network task-to-task (peer-to-peer). It is sad that DEC could not resolve the business issues effectively. Their tech was well ahead of its time in many ways.

~~~ 0;-Dan

---

