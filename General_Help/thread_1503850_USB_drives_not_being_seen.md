---
title: "USB drives not being seen"
date: 2010-06-07
forum: General Help
---

### Post by last1home on 2010-06-07
G'day,  running Ubuntu 10.04, works fine but does not recognise any drives connected via USB. Does if Ubuntu is run from live CD.

I looked through the forum and have found this problem aired but not seen any tangible answers; my apologies if I have missed some which gave a fix. Don't need to run scripts in terminal and tread water. There must be an answer. If an old lady needed to use an USB drive after she had loaded Ubuntu and had this problem I'm sure she would just need to tick a couple of boxes, and yes, I have had a look at Ubuntu Tweak.

This problem is on my laptop and Desktop PC; have looked at the format area and have tried an USB type drive from a colleague; same result. 

Nice smooth Linux though.

Thanks

Just like to say now at the beginning of this thread that it is now fixed, so it's worth a scroll down.

---

### Post by Chesamo on 2010-06-07
The problem you're mentioning could have a variety of causes. Just for the sake of diagnosing, plug in your drive, wait 30 seconds, then enter the following command in Terminal: ```
sudo lshw -c disk
``` and paste the output here.

Sorry to disappoint you, but a lot of things in Ubuntu have to be fixed through the Terminal. Not everything has (or needs) a GUI fix.

---

### Post by Mark Phelps on 2010-06-07
Sorry to sound discouraging, but I too have found this to be a recent problem.  I replaced an old hard drive with a newer one and formatted the partitions on the new drive manually using the GParted LiveCD.

After installing 10.04 on the new drive, I booted from it and plugged in the old drive using a USB cable attachment.  Ubuntu was unable to see the drive!

Tried the same thing booting from 9.10 (the oldest Ubuntu version I have).  Same problem.  No icon on the desktop.  No entry in Places.

Went into the new Partitioning tool in 10.04 and while it COULD see the drive under USB devices, it was unable to make any sense of it.  And this is particularly distressing given that this drive was the one containing all my Jaunty-related partitions and data.

Now ... before anyone starts ranting on about how the "drive is bad", or how I "hooked it up wrong", or any other such stuff, let me point out two things.  First, I've been doing this stuff for A LONG TIME, so I know my way around disk hardware -- and was careful to try every single cable and jumper option available.

And second, plugged the same drive, using the same cable attachment, into a Win7 machine -- and it recognized it right off!  

This really surprised me because, in the past, it was always the Linux OS, and/or the Linux utilities that could read a drive and it was MS Windows that had the problems.

So, sorry, don't have a solution for not being able to read drives connected via USB cables -- that is, using Ubuntu to do it.

---

### Post by barroy on 2010-06-07
*-disk                  
       description: ATA Disk
       product: HITACHI HTS54322
       vendor: Hitachi
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: FBEZ
       serial: 090621FB2F32YLHJJ96B
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=ed1f86f7
  *-cdrom
       description: DVD-RAM writer
       product: DVDRAM GSA-T50N
       vendor: HL-DT-ST
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: RE05
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc
  *-disk
       description: SCSI Disk
       product: 10EAVS External
       vendor: WD
       physical id: 0.0.0
       bus info: scsi@6:0.0.0
       logical name: /dev/sdb
       version: 1.75
       serial: WD-WCAU46558055
       size: 931GiB (1TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=4 signature=e8900690


terminal isnt a problem, ive used dos before, back in't day

---

### Post by last1home on 2010-06-08
G'day,
Thank you  for the  responses.

---

### Post by timgood on 2010-06-08
I had the same problem following an upgrade to 10.04 from 9.10. I solved it by uninstalling pmount, and then re-installing it together with libpmount0.0

Hope this helps.

---

### Post by last1home on 2010-06-08
timgood              **Re: USB drives not being seen**
         I had the same problem following an upgrade to 10.04 from 9.10. I  solved it by uninstalling pmount, and then re-installing it together  with libpmount0.0


[SIZE=4][COLOR=Red]Fixed[/COLOR][/SIZE]. Thank you timgood of Dawlish. Machines now  recognise all drives using USB  and displays icons on desktop from bootup and during machine running.



Thanks. last1home

---

