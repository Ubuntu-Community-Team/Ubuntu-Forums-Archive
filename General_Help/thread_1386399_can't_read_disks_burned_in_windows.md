---
title: "can't read disks burned in windows"
date: 2010-01-20
forum: General Help
---

### Post by poldie on 2010-01-20
I've already posted this but it didn't turn up!

I've got a brand new 9.10 64 bit Ubuntu.  But I can't read any disks I burnt under XP when I had a dual boot system.  Now I have an Ubuntu host and windows in a VM and I can't read my old disks in either.  It's the same physical pc, and I can watch regular DVDs in ubuntu, so the device itself is wired up and working.  I can only assume it's a problem with the disk format.  I burnt most of my (hundred of) disks using CdBurnerXP, which is free and great. I think all the disks were finalized (i know that's caused problems in the past).  The disks which I can't read under Ubuntu read just fine on my laptop.  This is a showstopper - I have to be able to read these disks otherwise I'm going to have to revert to a dual boot system which I'd really love to avoid (the plan is to have Ubuntu for everything except some Windows stuff which will be isolated on a VM).

Any ideas?

---

### Post by phillw on 2010-01-20
Hi,

have you got cdburnerxp installed in ubuntu ?

If not, try putting it on. --> [http://allmyapps.com/app/windows-7/cdburnerxp-cd-burning](http://allmyapps.com/app/windows-7/cdburnerxp-cd-burning)  Says it runs with Ubuntu.

Regards,

Phill.

---

### Post by poldie on 2010-01-20
> **phillw said:**
> Hi,

have you got cdburnerxp installed in ubuntu ?

If not, try putting it on. --> [http://allmyapps.com/app/windows-7/cdburnerxp-cd-burning](http://allmyapps.com/app/windows-7/cdburnerxp-cd-burning)  Says it runs with Ubuntu.

Regards,

Phill.

How would that help me to read the hundreds of DVDs I've burnt over the years?

---

### Post by phillw on 2010-01-20
> **poldie said:**
> How would that help me to read the hundreds of DVDs I've burnt over the years?

Well, my simple logic states ... If it **wrote** the darn things, it should be nice enough to **read** the darn things ?

Just a thought.

Regards,

Phill.

---

### Post by poldie on 2010-01-21
> **phillw said:**
> Well, my simple logic states ... If it **wrote** the darn things, it should be nice enough to **read** the darn things ?

Just a thought.

Regards,

Phill.

So.. to watch a video from a DVD I'd load up VLC, load up CDBurnerXP..uh.and then.....  lol.  Not going to work, is it?  Also, I don't understand why you think CDBurnerXP works under Ubuntu when it's a Windows app.

Anyone else have any ideas about how I can read these disks from Ubuntu?

---

### Post by rnerwein on 2010-01-21
hi
you think it's only aproblem with the disk format i think this too. but what's the format you burned the disk and which player you use on the ubuntu side. think there is only a plugin missig. but when we don't know your format - we can't help.
ciao

---

### Post by jamesisin on 2010-01-21
It is (and has been for some time) possible to run Windows applications on Unix systems using WINE.  I'm sure that's what he was getting at.

Have you tested these discs on any other computer aside from the machine on which they were originally burnt?

---

### Post by bumanie on 2010-01-21
Have you installed multi-media codecs? If not go [here]("https://help.ubuntu.com/community/Medibuntu") and follow the directions.

---

### Post by flabdablet on 2010-01-21
Given that neither Ubuntu or a Windows VM can new read these discs in your PC, but they work OK on your laptop, another possibility is that your PC disc drive has picked now to start feeling old and tired; either that, or the discs themselves are deteriorating and your laptop drive is just better at reading marginal discs than your PC drive is.

If it's an actual incompatibility between discs and drive, as opposed to some odd filesystem issue caused perhaps by CdBurnerXP, then you will see disc errors when you attempt to read the discs at a block level using a tool like [Gnu ddrescue.]("http://www.gnu.org/software/ddrescue/ddrescue.html") After installing it using```
sudo apt-get install gddrescue
```you can make it scan a disc for errors by attempting to copy it to /dev/null (the inbuilt information black hole) as follows:```
ddrescue /dev/cdrom /dev/null ddrescue.log
```

If ddrescue can scan the whole disc without errors, you can rule out bad discs and bad drives, and concentrate on solving the filesystem incompatibility issue. On the other hand, if ddrescue reports a bunch of disc errors, you know you need to try switching out your DVD drive.

---

### Post by poldie on 2010-01-21
> **jamesisin said:**
> It is (and has been for some time) possible to run Windows applications on Unix systems using WINE.  I'm sure that's what he was getting at.


No, he misread a link on that page to other, different Ubuntu software as meaning that CDBurnerXP ran under Ubuntu.

> **jamesisin said:**
> Have you tested these discs on any other computer aside from the machine on which they were originally burnt?

Yes - from my original post:

"The disks which I can't read under Ubuntu read just fine on my laptop."

---

### Post by poldie on 2010-01-21
> **flabdablet said:**
> Given that neither Ubuntu or a Windows VM can new read these discs in your PC, but they work OK on your laptop, another possibility is that your PC disc drive has picked now to start feeling old and tired; either that, or the discs themselves are deteriorating and your laptop drive is just better at reading marginal discs than your PC drive is.

If it's an actual incompatibility between discs and drive, as opposed to some odd filesystem issue caused perhaps by CdBurnerXP, then you will see disc errors when you attempt to read the discs at a block level using a tool like [Gnu ddrescue.]("http://www.gnu.org/software/ddrescue/ddrescue.html") After installing it using```
sudo apt-get install gddrescue
```you can make it scan a disc for errors by attempting to copy it to /dev/null (the inbuilt information black hole) as follows:```
ddrescue /dev/cdrom /dev/null ddrescue.log
```

If ddrescue can scan the whole disc without errors, you can rule out bad discs and bad drives, and concentrate on solving the filesystem incompatibility issue. On the other hand, if ddrescue reports a bunch of disc errors, you know you need to try switching out your DVD drive.

I will give that a go tonight - thanks.

---

### Post by poldie on 2010-01-21
> **bumanie said:**
> Have you installed multi-media codecs? If not go [here]("https://help.ubuntu.com/community/Medibuntu") and follow the directions.

Thanks, but I just checked that link and it looks like it's related to video formats (ie playing encrypted DVDs).  The disks I'm talking about contain data files - pdf, mp3, avi, source code etc.  I just want to be able to copy files from the DVDs onto my Ubuntu HD.

---

### Post by cascade9 on 2010-01-21
> **flabdablet said:**
> Given that neither Ubuntu or a Windows VM can new read these discs in your PC, but they work OK on your laptop, another possibility is that your PC disc drive has picked now to start feeling old and tired; either that, or the discs themselves are deteriorating and your laptop drive is just better at reading marginal discs than your PC drive is.

+1, IMO its either bad discs, a bad reader, or an evil combination of the 2. :|

I've had good luck with sony and pioneer CD/DVD drives being able to read discs that other drives cant. 

BTW, it might be an idea to backup your files to a different media. Hdds can last a lot logner than CD/DVDs

---

### Post by jamesisin on 2010-01-21
> Yes - from my original post:

"The disks which I can't read under Ubuntu read just fine on my laptop."

Sorry, I wasn't clear if that was a different machine or the same machine with a different build.

> Thanks, but I just checked that link and it looks like it's related to video formats (ie playing encrypted DVDs).  The disks I'm talking about contain data files - pdf, mp3, avi, source code etc.  I just want to be able to copy files from the DVDs onto my Ubuntu HD.

These are merely raw data discs you created yourself then?

Was Ubuntu able to read those discs when you were running your original dual-boot system?

I have seen issues with burning software (on XP) where it will only finish the disc well enough for certain machines (which is why I asked about other machines).

Let us know what happens with flabdablet's suggestion above.

---

### Post by GnubbyaBush on 2010-01-21
try installing VLC through wine, then load the disk that way...eh?

---

### Post by poldie on 2010-01-21
> **flabdablet said:**
> Given that neither Ubuntu or a Windows VM can new read these discs in your PC, but they work OK on your laptop, another possibility is that your PC disc drive has picked now to start feeling old and tired; either that, or the discs themselves are deteriorating and your laptop drive is just better at reading marginal discs than your PC drive is.

If it's an actual incompatibility between discs and drive, as opposed to some odd filesystem issue caused perhaps by CdBurnerXP, then you will see disc errors when you attempt to read the discs at a block level using a tool like [Gnu ddrescue.]("http://www.gnu.org/software/ddrescue/ddrescue.html") After installing it using```
sudo apt-get install gddrescue
```you can make it scan a disc for errors by attempting to copy it to /dev/null (the inbuilt information black hole) as follows:```
ddrescue /dev/cdrom /dev/null ddrescue.log
```

If ddrescue can scan the whole disc without errors, you can rule out bad discs and bad drives, and concentrate on solving the filesystem incompatibility issue. On the other hand, if ddrescue reports a bunch of disc errors, you know you need to try switching out your DVD drive.

I just tried that. I got no errors but it took 0 secs to run:

$ ddrescue /dev/cdrom /dev/null ddrescue.log

Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:         0 B,  errsize:       0 B,  errors:       0
Current status
rescued:      2048 B,  errsize:       0 B,  current rate:      170 B/s
   ipos:       512 B,   errors:       0,    average rate:      170 B/s
   opos:       512 B,     time from last successful read:       0 s
Finished                   

That disk has loads on it (a sql server 2008 iso for one thing!).

Some more info.  I'm sure the drive is fine.  This pc isn't that old (I built it myself). The drive worked fine until I installed Ubuntu over my old Ubuntu/XP dual boot. This is my desktop PC.  The install CD I used was burnt on my laptop using CDBurnerXP.  This disk is readable under ubuntu.  I have put in some older cds/DVDs which were almost certainly written on another pc/burner.   I can't get any disks which I know were burnt on this drive to read.  If it was a CDBurnerXP issue, then you'd expect the disks (such as the Ubuntu install disk) to not be readable.  Then again, that disk was burnt under XP running as a guest vm under Windows 7.  Some of the disks which I can't read on my desktop, work on the laptop. They're new disks, fairly recently burnt (last 6 months), so I can't see it being an age thing.  If there were such a thing as a live windows cd I'd boot from that and then try to read them on this drive!

Perhaps there's some way of rerunning that last test you had me do but making it read more. Perhaps it's not reading much because it too cannot see any evidence of any data on the disk because of a badly formed index table or something.   Is there some way of doing a low level read, but one which would fail if there were disk errors?

Update:  I've found some disks which were burnt on this drive in the last 6 months which work.  I've found some very old disks (almost 10 years old) which work.  I don't see any pattern yet. I'm going to keep trying (more disks) and see if I find one.  I can understand the idea that a drive might get old and have problems reading older disks but it's odd that it's only recently burned disks, burnt on that drive, which won't read, and much older disks are fine.

---

### Post by jamesisin on 2010-01-21
Build a live Windows CD?  You mean like this:

[http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)

---

### Post by cascade9 on 2010-01-22
> **poldie said:**
> I just tried that. I got no errors but it took 0 secs to run:

$ ddrescue /dev/cdrom /dev/null ddrescue.log

Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:         0 B,  errsize:       0 B,  errors:       0
Current status
rescued:      2048 B,  errsize:       0 B,  current rate:      170 B/s
   ipos:       512 B,   errors:       0,    average rate:      170 B/s
   opos:       512 B,     time from last successful read:       0 s
Finished                   

That disk has loads on it (a sql server 2008 iso for one thing!).

Looks to me like its not reading the disc. :| 

> **poldie said:**
> 
Some more info.  I'm sure the drive is fine.  This pc isn't that old (I built it myself). The drive worked fine until I installed Ubuntu over my old Ubuntu/XP dual boot. This is my desktop PC.  The install CD I used was burnt on my laptop using CDBurnerXP.  This disk is readable under ubuntu.  I have put in some older cds/DVDs which were almost certainly written on another pc/burner.   I can't get any disks which I know were burnt on this drive to read.  If it was a CDBurnerXP issue, then you'd expect the disks (such as the Ubuntu install disk) to not be readable.  Then again, that disk was burnt under XP running as a guest vm under Windows 7.  Some of the disks which I can't read on my desktop, work on the laptop. They're new disks, fairly recently burnt (last 6 months), so I can't see it being an age thing.  If there were such a thing as a live windows cd I'd boot from that and then try to read them on this drive!

Update:  I've found some disks which were burnt on this drive in the last 6 months which work.  I've found some very old disks (almost 10 years old) which work.  I don't see any pattern yet. I'm going to keep trying (more disks) and see if I find one.  I can understand the idea that a drive might get old and have problems reading older disks but it's odd that it's only recently burned disks, burnt on that drive, which won't read, and much older disks are fine.

I can see what your saying...but truthfully, I'm a little confused. Only data CDs your burnt from WinXP/CDburnerXP/new drive dont work? And your bootable ubuntu (from .iso) does? If that is the case, its still possible that CDburnerXPis causing the issue. 

BTW, just because its 'new' doesnt make the drive any good. I've had a junk burner (samsung IIRC) that seemed to burn just fine, but if you burnt at max speed it was always unreadable (40x for CD), if at about 20x it would burn fine of sony/verbatim discs but not on the yum-cha brandless stuff, and would only work on the cheapest media at x4 :| That drive was brand-new whne the problem started,a nd the owner didnt even realise it was doing that for a month or two (+25CDs and 25DVDs) 

Age and drive arent the only factors. Media and burn speed matter, a lot. If you burnt all the discs on your new system at max speed,and the media or the drive cant take max speed, then you can get bad burns. 

> **poldie said:**
> 
Perhaps there's some way of rerunning that last test you had me do but making it read more. Perhaps it's not reading much because it too cannot see any evidence of any data on the disk because of a badly formed index table or something. Is there some way of doing a low level read, but one which would fail if there were disk errors?

There probably is, but I dont know enough about ddrescue to know. 

I do have a different command. It wont scan for errors, but it should show how much data is on the disc, a few other things. 
[B][B]
isoinfo -d -i /dev/cdrom[/B][/B]  

With a data CD, the output tends to be like this- 

```
CD-ROM is in ISO 9660 format
System id: 
Volume id: MY_DISC
Volume set id: 
Publisher id: 
Data preparer id: 
Application id: NERO BURNING ROM
Copyright File id: 
Abstract File id: 
Bibliographic File id: 
Volume set size is: 1
Volume set sequence number is: 1
Logical block size is: 2048
Volume size is: 2145840
Joliet with UCS level 3 found
NO Rock Ridge present

```It should at least show if there is any data on the discs you have tried but it seems not to be reading. ;)

---

### Post by flabdablet on 2010-01-23
Could you post the contents of ddrescue.log?

After posting ddrescue.log, you should delete it before trying any more runs with ddrescue (or specify a different log file name in the ddrescue command line). Ddrescue looks at the specified log file before it starts in order to figure out what remains to be done, and if the log file reflects a fully completed copy run, it will do nothing at all.

Something else that's worth checking: /dev/cdrom is usually a symlink to the CD reader's real /dev entry. Could you also post the output of **ls -l /dev/cdrom** or check it yourself to make sure /dev/cdrom points to the correct device?

---

### Post by falconindy on 2010-01-23
> **flabdablet said:**
> Could you also post the output of **ls -l /dev/cdrom** or check it yourself to make sure /dev/cdrom points to the correct device?
'readlink -f /dev/cdrom' will get to the heart of the matter quicker as /dev/cdrom usually points to a yet another symlink (e.g. /dev/cd/cdrom-6:0:0:0). It should resolve as /dev/sr0 or /dev/hda.

When you load a "non-working" CD, do you hear the drive spin up? What's the output of 'mount' after loading the CD? What happens if you type "sudo mount /dev/cdrom" in a terminal?

---

### Post by poldie on 2010-01-24
> **falconindy said:**
> 'readlink -f /dev/cdrom' will get to the heart of the matter quicker as /dev/cdrom usually points to a yet another symlink (e.g. /dev/cd/cdrom-6:0:0:0). It should resolve as /dev/sr0 or /dev/hda.

When you load a "non-working" CD, do you hear the drive spin up? What's the output of 'mount' after loading the CD? What happens if you type "sudo mount /dev/cdrom" in a terminal?

Ok, putting a non-working disk in, the drive spins up.

Trying the readlink command gives me:
/dev/sr0

ls -l /dev/cdrom
gives me the permissions/dates etc, ending with:
/dev/cdrom -> sr0

isoinfo -d -i /dev/cdrom 
gives me:
isoinfo: invalid argument. Seek error on old image

sudo mount /dev/cdrom
gives me:
mount: block device /dev/sr0 is write-protected, mounting read only

it then pauses for 20-30 seconds, followed by:

mount: wrong fs type, bad option, bad superblock on /dev/sr0,
missing codepage or helper program, or other error
(could this be the IDE device where you in fact use ide-scsi so
that sr0 or sda or so is needed?)
in some cases useful info is found in syslog - try
dmesg | tail or so

And when i look at the end of syslog, I can see this:

[31090.056804] sr 4:0:0:0: [sr0] Unhandled sense code
[31090.056809] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[31090.056814] sr 4:0:0:0: [sr0] Sense Key : Medium Error [current] 
[31090.056819] Info fld=0x10
[31090.056821] sr 4:0:0:0: [sr0] Add. Sense: No seek complete
[31090.056826] end_request: I/O error, dev sr0, sector 64
[31090.056838] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16

(it would be easier if syslog had date/time down the side!)

ddrescue.log:

# Rescue Logfile. Created by GNU ddrescue version 1.11
# current_pos  current_status
0x00000000     +
#      pos        size  status
0x00000000  0x00000000  ?



> Only data CDs your burnt from WinXP/CDburnerXP/new drive dont 
> work? And your bootable ubuntu (from .iso) does? If that is 
> the case, its still possible that CDburnerXPis causing the 
> issue. 


I can't find any disks which don't work, other than those burnt on this drive recently.  The bootable ubuntu iso disk works, and was burnt on the laptop (which reads the disks I can't read on my desktop).  So yes, that's why i'm pointing the finger of blame at cdburnerxp, not the drive, although it could of course be the drive.  

I've had people give me CDs with photos on before which I couldn't read, then some months later it occured to me that the disks haven't been finalised, and once finalised I can read them.  I'm not sure if that was on this drive - i just mention it as an example of why a disk not being read on 1 drive needn't be the fault of the drive - it might be that the pc on which the cd could be read when it was not finalised might have had different firmware which handled the disk differently.

I always ignore the max burn speeds on the burner and disk - I rarely burn faster than x4.  I used cdburnerxp because I had trouble finding software which did a verify.  In fact, I reported the fact that verifying disks caused the app to crash for 2 linux burners (brasero and some other app), and it was because nothing was done about this that I reverted to burning stuff in Windows!

---

### Post by jamesisin on 2010-01-24
Have you tried burning a disc in the drive under Ubuntu to see if those come out working correctly?  I too think it's the application you were using but this test should be easy enough.

(In case you care, I usually burn about half of full speed to reduce uncaught burning errors--like movies that jiggle or skip.)

---

### Post by poldie on 2010-01-24
> **jamesisin said:**
> Build a live Windows CD?  You mean like this:

[http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)

I just tried that.  I want my 2 hours back!  The instructions didn't work - perhaps they assume 2 drives - the windows disk and the blank disk.  If you take the windows disk out when it's built and put the blank disk in it asks for the files!  Hasn't it just built the iso?  No.  So i had to do that again. Finally, when I boot up, nothing works.  I got a dos box up, then it stopped responding. I put my disk in and then I couldn't get a dos box up.  Etc.

Moving on to your most recent post, yes, I'll try and burn using brasero.  It'll give me a chance to see if they've fixed the bug where my machine hangs during verify!

---

### Post by Jackzor on 2010-01-24
> **jamesisin said:**
> Build a live Windows CD?  You mean like this:

[http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)

I don't know you.. But I don't like you :P

I was just going to post that. I remember using it years ago just playing with it and he said something about needing a windows xp live.. And there it is. I'm two days late for this thread I guess.

---

### Post by jamesisin on 2010-01-24
> **poldie said:**
> I just tried that.  I want my 2 hours back!

Sorry, man.  Of course it's working with MS, so you might try it exactly the same tomorrow and it will work.

---

