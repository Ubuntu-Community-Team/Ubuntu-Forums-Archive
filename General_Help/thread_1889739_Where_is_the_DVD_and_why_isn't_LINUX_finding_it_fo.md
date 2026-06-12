---
title: "Where is the DVD and why isn't LINUX finding it for me??!!"
date: 2011-12-01
forum: General Help
---

### Post by ffej2ffej on 2011-12-01
I burned a DVD.  It works.  I know it works.  It works in the external USB drive I used to burn it.  (using another OS) However, I start UBUNTU, either with the disk in the drive or not.  Either with the drive plugged in or not.  When the disk finishes spinning (indicating to me that it has discovered what it's got in there), UBUNTU does nothing.
When I open Banshee Media Player, it gives me no indication that it even knows about the external drive.
When I open Movie Player, the same thing.
I then opened a terminal window and looked in /mnt, /media and several other folders.  Needless to say I found nothing.  Please help!!

:mad:

---

### Post by fantab on 2011-12-01
> **ffej2ffej said:**
> I burned a DVD.  It works.  I know it works.  It works in the external USB drive I used to burn it.  (using another OS) However, I start UBUNTU, either with the disk in the drive or not.  Either with the drive plugged in or not.  When the disk finishes spinning (indicating to me that it has discovered what it's got in there), UBUNTU does nothing.
When I open Banshee Media Player, it gives me no indication that it even knows about the external drive.
When I open Movie Player, the same thing.
I then opened a terminal window and looked in /mnt, /media and several other folders.  Needless to say I found nothing.  Please help!!

:mad:

if your other OS is Windows, remember that Autorun.exe does not work in Linux. 

Does nautilus find it? I mean can you see the DVD listed in the left hand panel when you open HOME? If you can see click on it to open it.

Do other DVD's work?

---

### Post by killermist on 2011-12-01
You could try 
```
ls -l /dev/dvd*
```
If it doesn't show up there, then the drive isn't being detected.

If the drive is being detected, it may not be being auto-mounted.
Does your filemanager offer an option to look at drives?
For example, in pcmanfm, in the left pane, it shows several "quick pick" locations followed by mounted and unmounted drives.  If I choose any of the unmounted drives from the list, it mounts it for me (if it can) and then browse into it.

---

### Post by ffej2ffej on 2011-12-01
> **killermist said:**
> You could try 
```
ls -l /dev/dvd*
```If it doesn't show up there, then the drive isn't being detected.

If the drive is being detected, it may not be being auto-mounted.
Does your filemanager offer an option to look at drives?
For example, in pcmanfm, in the left pane, it shows several "quick pick" locations followed by mounted and unmounted drives.  If I choose any of the unmounted drives from the list, it mounts it for me (if it can) and then browse into it.

So far, so good. In terminal, I typed the ls command stated above.  It listed 3 devices and I tried to mount all 3 of them.  Terminal told me "can't find [whichever device] in /etc/fstab or /etc/mtab.
I then typed pcmanfm, and it told me this program was not installed but could be using sudo apt-get.  I did so.  
When I started pcmanfm, it showed the drive.  No doubt about it.  I clicked on the drive and found two folders: one for audio and one for video.
This disk is a DVD, the kind you get from Blockbuster or RedBox or someplace like that.  
I think to summarize, we have proven that the hardware is working and UBUNTU recognizes it.  Now, I need it to recognize it as a movie (like Winderz and OSX do) and play it.

---

### Post by Chronon on 2011-12-02
Any reason you installed pcmanfm?  Nautilus is the default file manager for Ubuntu.  After mounting the volume what happens when you try to play the disc with your media player?

---

### Post by ffej2ffej on 2011-12-02
> **Chronon said:**
> Any reason you installed pcmanfm?  Nautilus is the default file manager for Ubuntu.  After mounting the volume what happens when you try to play the disc with your media player?

Much as I hate to admit, the reason I installed pcmanfm is someone told me to and I'm that much of a rookie in UBUNTU (or any form of Linux for that matter).  
Prior to installing pcmanfm, I saw no evidence of the DVD either in "home folder" nor "file system" nor many, many folders from the terminal. *See the 1st message in this thread.*
Thanks for the help I've received so far, maybe by the end of the year I'll be able to watch "The Music Man" on this computer once and for all.  (We got _TROUBLE_ my friends!)

---

### Post by grahammechanical on 2011-12-02
This could be an issue with not having the right codec installed. When you installed 11.10 did you check the box to authorise the install process to download proprietary codecs from Fluendo? You might need to install Ubuntu Restricted Extras from the UBuntu Software Centre.

Let us discount this as the problem if we can.

Regards.

Another idea is to open System Settings>Removable Media and make sure that under the list for Select how media should be handled DVD Video is not set to Do Nothing.

---

### Post by ffej2ffej on 2011-12-02
> **grahammechanical said:**
> This could be an issue with not having the right codec installed. When you installed 11.10 did you check the box to authorise the install process to download proprietary codecs from Fluendo? You might need to install Ubuntu Restricted Extras from the UBuntu Software Centre.

Let us discount this as the problem if we can.

Regards.

Another idea is to open System Settings>Removable Media and make sure that under the list for Select how media should be handled DVD Video is not set to Do Nothing.
First of all, (I'm not kidding!) did Bill Gates decide he hasn't ruined anything lately and needed to inflict his "magic" on Linux??!!  I cannot believe something that should be completely automatic is causing me to perform all these steps and STILL DOESN'T WORK!@!
Here is the latest status.
I never saw an option to install anything optional when I installed UBUNTU, so obviously I did not install any optional codecs. However, after I read the last message in this thread, I went to the UBUNTU Software Center and installed the Restricted Extras.  Before it installed, it warned me that it would remove 2 other codecs in order to do this.  I still have faith in UBUNTU, so I let it.  
After the install, I did a full, power off, cold re-boot just to make sure.
Upon re-starting, I found nothing had changed.  Nautilus does not show the drive at all until I start pcmanfm. Then, the drive shows in pcmanfm and Nautilus and everywhere else.  It still will not play the expletive expletive movie. 
I tried adjusting the system settings to all the possible choices.  The closest I can get is the following.  I start the system and no evidence of the disk or the drive is present.  I open a terminal window and start pcmanfm and suddenly the drive appears with the disk in it.  If I eject the disk (using either the icon in Nautilus or the icon in pcmanfm or the button on the front of the drive) and then re-insert the disk, something will **finally** prompt me to ask what I want to do with this MOVIE DVD.  Whether I tell it to open in Movie Player or Banshee, it does the same as it did before: it opens the program I choose which still has no idea that there is a MOVIE DVD in the drive.
Does NE1 know how to get in touch with the Amish?  I'm sick of this!!

---

### Post by MG&amp;TL on 2011-12-02
> **ffej2ffej said:**
> First of all, (I'm not kidding!) did Bill Gates decide he hasn't ruined anything lately and needed to inflict his "magic" on Linux??!!  I cannot believe something that should be completely automatic is causing me to perform all these steps and STILL DOESN'T WORK!@!


You have to remember that linux is free and cannot afford to pay for the codecs, etc. required to play dvds. Therefore DVDs are likely to be buggy, requiring a little more attention. You'll get there in the end. :)

---

### Post by pqwoerituytrueiwoq on 2011-12-02
have you done this?
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by ffej2ffej on 2011-12-02
> **pqwoerituytrueiwoq said:**
> have you done this?
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

I have now.  Still no change, though.

---

### Post by ffej2ffej on 2011-12-02
> **pqwoerituytrueiwoq said:**
> have you done this?
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

I followed all the instructions on the page referred by that link.  Nothing has changed.  The drive will not be found or mounted by Nautilus.  pcmanfm will make the drive visible to everything everywhere, but none of the programs that are supposed to will recognize it as a movie.  Even if I eject the disk then re-mount it, the resulting dialog will offer to open Movie Player or Banshee.  When either of those programs opens, they act as though they were opened from the launcher or the terminal window.  That is, they have no idea that they were opened with intent to play the DVD.
Neither program "gets it" when I try to open or import the DVD, either.
I guess for now, this is as close as I'm going to get.

---

### Post by fantab on 2011-12-02
What format the movie on DVD is in? Have you installed VLC Media Player? I have not installed any restricted formats from Ubuntu, yet VLC plays them all except off course VCD. All DVD works out of the box.

You haven't replied to:
Does Ubuntu on your computer play other DVD? Or is this just one DVD we are trying to sort out?

---

### Post by killermist on 2011-12-02
VLC and mplayer are good media players, and often have DVD playback abilities built in.

Did you say that you have multiple DVD and/or optical drives?  That could confuse some players if the drive you're trying to use isn't at the same device location as the player expects by default.

What is the output of ```
mount
```

---

### Post by oldtimer7777 on 2011-12-02
> **ffej2ffej said:**
> I burned a DVD.  It works.  I know it works.  It works in the external USB drive I used to burn it.  (using another OS) However, I start UBUNTU, either with the disk in the drive or not.  Either with the drive plugged in or not.  When the disk finishes spinning (indicating to me that it has discovered what it's got in there), UBUNTU does nothing.
When I open Banshee Media Player, it gives me no indication that it even knows about the external drive.
When I open Movie Player, the same thing.
I then opened a terminal window and looked in /mnt, /media and several other folders.  Needless to say I found nothing.  Please help!!

:mad:

Do you have all your dvd codecs installed? 

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

It is about 1/3rd the way down the checklist...

---

### Post by ffej2ffej on 2011-12-03
> **killermist said:**
> VLC and mplayer are good media players, and often have DVD playback abilities built in.

Did you say that you have multiple DVD and/or optical drives?  That could confuse some players if the drive you're trying to use isn't at the same device location as the player expects by default.

What is the output of ```
mount
```

Here are the results of the mount command in terminal:

/dev/sda5 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jeff/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jeff)

I have no idea what any of this means nor do I think I should.

---

### Post by oldos2er on 2011-12-03
Did you have a DVD in the drive when you ran **mount**? How many DVD drives to you have, and how are they connected? I.e., USB, SATA, etc.

If you could provide answers to the questions asked of you in posts #13 and #14 it will help us help you.

---

