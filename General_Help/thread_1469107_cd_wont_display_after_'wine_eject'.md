---
title: "cd wont display after 'wine eject'"
date: 2010-05-01
forum: General Help
---

### Post by compiz addict on 2010-05-01
I'm installing a program in WINE that requires more than 1 CD. I used wine eject to unmount the first one, and now ubuntu wont read the second one. No errors or anything, the drive just spins for a bit, then stops, and then the icon for the second cd doesn't appear, and I still have this wonderful message "Please insert disk number 2".

---

### Post by compiz addict on 2010-05-01
just gonna bump this so any late-night forum-ers will catch this thread.

---

### Post by mc4man on 2010-05-01
Sorry about not thinking thru that if you're running lucid it's most likely wine doesn't even 'know' about your cd/dvd drive.

(The wine eject command should not of worked

If you did a fresh install of lucid then there will be no fstab entry for your drive(s) and wine can't address it.

Is this the case?

I just did a multi-disc install on lucid 2 different ways so it's possible.

The first way (without an fstab entry), I created a 'drive' in winecfg - D: with an address matching the mount point of the cd - /media/<volumelabel> and proceeded as normal

The second way,  I created a fstab entry, restarted, had winecfg detect the drive and again no issue

---

### Post by compiz addict on 2010-05-01
I did install Lucid, but I did it through the Update manager. End the eject thing worked fine, but when I put the next disk in (or any other disk), it wouldn't mount automatically, and I'm not 100% sure how to mount it ('sudo mount /dev/hdc' didnt work).

---

### Post by mc4man on 2010-05-02
```
End the eject thing worked fine
```
Well that makes this a bit 'confusing' - a combo of 'bad' behavior by the update - leaving the previous fstab entry, the improper enforcing of the 'executable bit' deal on .exe's on cdrom's, and possibly no mount directory as specified in your fstab.

Do this
with the cd in the drive run this and post what's shown in the *-cdrom: entry
```
sudo lshw -C disk
```

Also post this
```
cat /etc/fstab
```

And could you look in /media to see if a cdrom0 directory exists

---

### Post by compiz addict on 2010-05-02
Ok, here is is:
```

*-cdrom
       description: DVD-RAM writer
       product: DVD-RAM GSA-H55N
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/Sims2_1
       version: 1.05
       serial: [HL-DT-STDVD-RAM GSA-H55N1.0507/12/11 7U02
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted status=ready

```

And heres my fstab file:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=38981be6-73af-4394-8471-5d4ee3e43e37 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=c14ad2ec-9a93-4e58-a401-b290b0e16fb1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

And in my /media directory I do have cdrom, cdrom0, and a cdrom1, yet I only have 1 cd drive (but I have a multicard reader, so I think that's why), and I also have Sims2_1, which is disk 1 for my Sims install. Also, I have one called thd, but I don't think that one matters.

Also, as soon as I eject or unmount Sims2_1, this goes away from the *-cdrom thing: "logical name: /media/Sims2_1". After that I have to restart my computer for it to read disks again.

---

### Post by compiz addict on 2010-05-02
just quick bump so people don't miss this

---

### Post by mc4man on 2010-05-03
Well, for a multi disk install thru wine the drive or mount point must be recognized by wine.
There are 2 ways I've tested successfully (see edit

One is a correct fstab entry for the drive

```
gksu gedit /etc/fstab
```

Change /dev/hdc to /dev/sr0
The line would look like this
```
/dev/sr0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

Then do a restart, after which open winecfg -> drives -> autodetect (you should see a D: drive created with a path of /media/cdrom0), click 'apply' and then try your install again

The other is to create a drive letter in winecfg that points to the mount point - in this case /media/Sims2_1
For instance create a D drive with mountpoint (path) of /media/Sims2_1

screen shows (click add - then fill in path box, click apply

Then from terminal (replacing blue with actual name of the sims setup or install exe
```
wine D:/[COLOR="Blue"]Setup.exe[/COLOR]

```
When the first disk is done use the eject button on drive, put in 2nd disk, after it settles click ok or whatever in the prompt for 2nd disk box.

If trying the 2nd method I'd comment out the fstab line, as such
```
#/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```


Edit:
if done correctly both methods will work - which is the 'better' one I can't say

As perspective - a fresh install of lucid will have no fstab entries for cd/dvd drives, but clearly upgrade installs will, ( and as seen in your case an improper line for your drive

What the actual intention is I don't know, it seems to me to be a flaw in the upgrade install that should be addressed or maybe it can't be addressed ..?

On a test install (fresh) I've added an fstab entry with no ill effects - but you don't have a 'fresh' install
> After that I have to restart my computer for it to read disks again.
that is a bit of a concern - you'll have to see which way is best for you.

Side note - the reason your drive has dev links of dev/dvd1, /dev/cdrom1 ect. is that in udev you probably have 2 entries for the same drive - /dev/hdc and /dev/sr0
This isn't a big issue. (more of a 'housekeeping' thing if true), if you wish to check this out and clean that up let me know  - will return the drive to /dev/dvd and /dev/cdrom, ect.

(it's possible there is only 1 entry in udev but the upgrade install up'ed the link numbers - no matter,  if you wish the more typical links (some apps will default to /dev/dvd, dev/cdrom), that can be fixed

---

