---
title: "unable to mount audio cd on  karmic"
date: 2009-11-17
forum: General Help
---

### Post by swdinesh on 2009-11-17
I tried to mount audio cds but I always obtain the errors a posted below and no possibility to mount the audio cd 

anyone can help me about that?

thank you 
Alex

errors from messages.log

kernel: [166213.161816] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
kernel: [166213.161824] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
kernel: [166213.161831] Info fld=0x20, ILI
kernel: [166213.161834] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
kernel: [166213.161847] __ratelimit: 68 callbacks suppressed
kernel: [166213.168945] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
kernel: [166213.168953] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
kernel: [166213.168960] Info fld=0x20, ILI
kernel: [166213.168962] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
kernel: [166213.290531] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
kernel: [166213.290540] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
kernel: [166213.290547] Info fld=0x0, ILI
kernel: [166213.290550] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
kernel: [166213.292813] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
kernel: [166213.292821] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
kernel: [166213.292828] Info fld=0x0, ILI
kernel: [166213.292830] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
kernel: [166213.294497] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
kernel: [166213.294505] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
kernel: [166213.294511] Info fld=0x0, ILI
kernel: [166213.294513] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track

---

### Post by mc4man on 2009-11-17
What you're showing is typical from inserting an audio cd, maybe go look and see if the files are present (home folder -> .gvfs/cdda mount on sr0

From inserting audio cd here (which shows up and plays fine

> doug@doug-laptop:~$ dmesg | tail
[ 4804.037396] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4804.037410] sr 3:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 4804.037423] Info fld=0x0
[ 4804.037429] sr 3:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 4804.037443] end_request: I/O error, dev sr0, sector 0
[ 4804.042508] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4804.042519] sr 3:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 4804.042529] Info fld=0x0
[ 4804.042534] sr 3:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 4804.042547] end_request: I/O error, dev sr0, sector 0
doug@doug-laptop:~$ ls ~/.gvfs/'cdda mount on sr0'
Track 1.wav  Track 3.wav  Track 5.wav  Track 7.wav
Track 2.wav  Track 4.wav  Track 6.wav  Track 8.wav


---

### Post by swdinesh on 2009-11-17
I have no file in that directory :(

even waiting some time after the cd is inserted 

can i do something about that?

Thx
Alex

---

### Post by mc4man on 2009-11-17
with a disk in the drive run this and see what's shown in the *-cdrom section
```
sudo lshw -C disk
```

Do other disks work?, if you have any available (data cd/dvd's, dvd video

---

### Post by swdinesh on 2009-11-17
ather kind of disks are fine (dvd like data cd/dvd)

the output is 
  *-cdrom
       description: DVD reader
       product: CDRW/DVD GCCT10N
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: A100
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=ready


I have another cddrive mounted and the putput for it is:

*-cdrom
       description: DVD-RAM writer
       product: DVDRRW GSA-2166D
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@8:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: 1.00
       serial: [HL-DT-STDVDRRW GSA-2166D1.0005/07/25
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: status=nodisc

---

### Post by swdinesh on 2009-11-18
I don´t know why ...but now it´s working good 

...this is a mistery :( 

Alex

:P:P:P

---

### Post by jjbailey on 2010-01-17
I have been googling for an answer to my problem, which is seemingly identical to the one swdinesh had. All except for it having yet to mysteriously fix itself. I had been using Jaunty and decided to upgrade to Karmic via Update Manager. That upgrade pooched itself and so I did a clean install of Karmic on another partition so I could salvage my stuff. 

Now I can't access audio CDs on the fresh install. Data CDs and everything else mounts fine. The CD Drive icon in Nautilus is visible until I insert an Audio CD, then it disappears and will not reappear until I eject it. Nothing appears in /mnt or /cdrom, or any audio apps. However the drive seems to be reporting a disc when present. Any help would be great. Thanks.
With disk:
```
*-cdrom                 
       description: CD-R/CD-RW writer
       product: CD-Writer+ 9500
       vendor: HP
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.0e
       serial: [HP      CD-Writer+ 9500 1.0e Jul19 ,  MYC25HD
       capabilities: removable audio cd-r cd-rw
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
```Without disk:
```
*-cdrom                 
       description: CD-R/CD-RW writer
       product: CD-Writer+ 9500
       vendor: HP
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.0e
       serial: [HP      CD-Writer+ 9500 1.0e Jul19 ,  MYC25HD
       capabilities: removable audio cd-r cd-rw
       configuration: ansiversion=5 status=nodisc

```

---

### Post by jjbailey on 2010-01-18
<bump> Can anybody help me? Audio CDs worked fine for me in Hardy and Jaunty, now they don't in Karmic. Nothing in any apps: rhythmbox, nautilus, xmms, etc.

---

### Post by genterminl on 2010-04-18
I'm having similar problems.  Lots of the same errors in dmesg.  DVDs seem to play the video OK, but audio is choppy/static and completely garbled - same with audio CDs.  Currently this is with a DVD-ROM and DVD-RW drive, both new, because I was having the same problems with a CD-ROM and different DVD-RW drive.  DVD disks even get correctly auto-mounted.  Sound from files or streaming work OK (sometimes fine, and sometimes a little choppy, but nothing like trying to play from disk).  All the same with mplayer, vlc, xine, rhythmbox.

Karmic 9.10, kernel 2.6.31-20-generic.

I haven't tried burning either CD or DVD yet.  Per some other threads, I uninstalled brasero, but no change.  Per another thread, I killed the "hald-addon-storage: polling /dev/sr0 (every 2 sec)" process (also for sr1) with no change in behavior. 

I've confirmed that the disks are read fine in other PCs.

I'll be glad to post any logs, but I don't see any significant differences from the samples already posted.  

There are lots of posts about this - with some range of symptoms, but no solutions.  I have no problem ejecting disks or mounting disks, just read errors in the logs, and really bad audio playback.

I'd really love some solid ideas on how to figure out what the real problem is.

Jack

---

### Post by mutantstargoat on 2010-07-17
So I guess this is still not working?

---

### Post by genterminl on 2010-07-17
Now on 10.04, with 2.6.32-22 kernel, and still essentially the same behavior.

Just now I tried an audio CD - the sound was better than I remember, but still kind of choppy, withe the same type of errors in dmesg for both audio-CD and DVD.

---

### Post by mghis on 2010-07-25
Same problem! I see the files after installation and compile of 'cdfs-src' package, but i cannot play the files on the cd.
:(

---

### Post by Jay Christnach on 2011-04-12
I have still a similar problem with skipping playback of audio cds (see my other post in the multimedia forum).

But I have been able to solve the dvd-video-reading problem by installing libdvdcss2. It's the library responsible for playing scrambled sectors.

I hope this helped at least partly. Please let me now if you find a solution to the audio cd problem.

BTW audio cds don't get mounted. They are read by raw access to the disk.

kind greetings!

---

### Post by Chris7 on 2011-10-08
Any solutions for this problem?

---

