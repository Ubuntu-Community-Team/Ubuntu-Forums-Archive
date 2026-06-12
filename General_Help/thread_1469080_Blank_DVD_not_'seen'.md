---
title: "Blank DVD not 'seen'"
date: 2010-05-01
forum: General Help
---

### Post by drhiii on 2010-05-01
10.4 upgrade went very well, except for CD/DVD issues.

Upgraded from 9.10.  Was able to insert blank DVDs and have a popup appear asking what to do.  Same response for data DVDs, and movies just played.

After upgrade, all this behavior went away.  Placing a blank DVD into the drive bay, nothing.  I can place a data DVD into the bay on one machine (upgraded two computers), it sees the data.  I cannot play movies.  

Have been reading through posts to see if I can free up the issue.  Tried MountManager to give permissions to 'Everybody' on all devices but that didn't work.  It certainly did rewrite my /etc/fstab tho!

Anyone point me to some solutions?  I know it will be something simple.  Am just not getting it yet.

tx for any help

---

### Post by drhiii on 2010-05-01
Here is my fstab after 10.4 upgrade:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2240e045-c230-44f1-bb49-51439d8c65ae /               ext4    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=753b9fc8-c980-49ec-9421-a0e25f9f7503 none            swap    sw              0       0
#UUID=8bb0884a-ce0a-44a5-b1cf-00c02e29e5f3   /media/sdb  ext3   defaults 0 0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1	/media/sdb	ext3   defaults 0 0

/dev/sdc1	/media/500gb	ext3	relatime	0	0



Here is fstab after MountManager got ahold of it:

UUID=2240e045-c230-44f1-bb49-51439d8c65ae / ext4 defaults 0 1
UUID=753b9fc8-c980-49ec-9421-a0e25f9f7503 swap swap sw 0 0
UUID=29968b24-7c49-4251-93d3-f64bf8dcba5c /media/sdb ext3 defaults 0 0

---

### Post by drhiii on 2010-05-01
More info.  This is what is reported using    sudo lshw -C disk


*-cdrom
       description: DVD-RAM writer
       product: DVDRW LH-20A1H
       vendor: LITE-ON
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom0
       version: LL0B
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,utf8 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/cdrom0
          configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,utf8 state=mounted

---

### Post by WorMzy on 2010-05-01
Open up nautilus and goto: Edit -> Preferences -> Media, under "Other Media", select "blank DVD disk", and make sure that "Ask what to do" is selected, and not "Do nothing".

That's all I can think of.

---

### Post by drhiii on 2010-05-02
> **WorMzy said:**
> Open up nautilus and goto: Edit -> Preferences -> Media, under "Other Media", select "blank DVD disk", and make sure that "Ask what to do" is selected, and not "Do nothing".

That's all I can think of.

Thank you for your response... 

<EDIT>  Right after I sent it, I found the Media tab and was able to review the settings.  They all look correct.  Didn't see something that referred to blank media tho...
</EDIT>


Now I am going to ask a really dumb question.  How do I open up Nautilus?  Isn't that the file manager?  If it is, I don't see the CD/DVD drive unless something is in it, which is part of the problem 'cause it doesn't seem to be recognized.

Again, appreciate your help.  Am stumbling around trying to tweak what I think will be a simple fix.  Just don't know it yet, sigh.

---

### Post by WorMzy on 2010-05-02
Yep, it's the file manager. Just open your home folder or something (the folder you do it from doesn't matter) and follow the instructions in my previous post.

About not being able to play DVDs, you probably need to install libdvdcss2 from medibuntu, here's a howto on that: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by WorMzy on 2010-05-02
Did you look under other media? Click on the Type box.

[[IMG]http://www.ubuntu-pics.de/thumb/55712/file_management_preferences_010_bkftoa.png[/IMG]]("http://www.ubuntu-pics.de/bild/55712/file_management_preferences_010_bkftoa.png")

---

### Post by wilee-nilee on 2010-05-02
I have the same thing happen no blank DVD seen, but it can be written to when you use gnomebaker or brasero at least for me.

---

### Post by drhiii on 2010-05-02
> **WorMzy said:**
> Did you look under other media? Click on the Type box.

[[IMG]http://www.ubuntu-pics.de/thumb/55712/file_management_preferences_010_bkftoa.png[/IMG]]("http://www.ubuntu-pics.de/bild/55712/file_management_preferences_010_bkftoa.png")


Ah, now I get it!  I am looking into this now.  I was finally able to try and 'burn' a DVD, but I continue to get odd behavior, like it was unable to eject DVD after burning which it had done before.  At least it saw the blank DVD.  But I have to reboot each time to have it see a new DVD.

I will keep messing with it as it has to be some setting that has taken hold of my machine wants to be a legacy pain in the **** thing...

Appreciate your continued response.  It helps us neophytes know we aren't completely alone.  Ubuntu it sooooooooo way worth it because of this community...

---

### Post by drhiii on 2010-05-02
Ok ok... I think this may have unlocked the mystery.

It appears the /etc/fstab had a line in it, left over from what I don't know, but it was trying to 'find' that device during boot.  It kept forcing me to override it which I did, but I know see doing that bollixed up the system's ability to find any other device after booting. 

Once I commented that line out, things started to behave properly.  At least, so far.

This is good for me, but I can see where if there was a legacy line left in fstab, a total newb would be lost.  I have at least enough ability to get in and out, and in trouble.  

Now, I just have to figure out how to retitle this thread as 'SOLVED'.  (EDIT: I solved the SOLVED How To)

I appreciate everyone who took the time to respond (esp WorMzy).  This is why I am into Ubuntu, and promote it to anyone who will listen.  Because of this community...  the 9.10 to 10.4 upgrade was brilliant (so far), and this blip is hardly a blip considering what gets handed to us every 6 months.  This is hardly painful considering what I know other people and their OS choices go through.  And I learned several new things I never knew before.

Thank you Ubuntu, and this community.

---

### Post by WorMzy on 2010-05-02
I'm glad you managed to get it sorted. :)

---

