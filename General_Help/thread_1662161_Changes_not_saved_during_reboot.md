---
title: "Changes not saved during reboot?"
date: 2011-01-07
forum: General Help
---

### Post by chargersfan420 on 2011-01-07
I seem to be having an odd problem.  I created an entry in my "Startup Applications" menu about a week ago that loads some video wallpaper.  Afterwards, I rebooted and the entry was gone.  Then another reboot and it had returned, and yet another reboot and it was gone again.

I created the entry a second time, and it seemed to stick around for good (at least 5-6 reboots).  Then I decided to use a different wallpaper so I changed the menu entry to point to a different file.  After rebooting, it was back to the first file.  Then on my next reboot it was pointing to the second file, as it should have been.  Two more reboots since have it pointing back to the first file.

I have also seen it do this with other files I have modified, specifically /etc/fstab.  Sometimes my changes stick, sometimes they don't, and sometimes they show up again after not showing up during the last reboot.

Since I have no idea what could be causing this problem, I will try to post some details of my system here.  If more details are required, please ask!

Ubuntu 10.10 64-bit
Using kernel 2.6.35-24-generic
/ and /home are separate partitions, both are ext4.  These partitions were created by the install CD.
Both partitions exist on the same physical disk, a 7200 RPM 500GB SATA drive.
Machine is an Alienware M17x-R2 laptop.

---

### Post by chargersfan420 on 2011-01-10
Bump!

Nobody has any ideas, or also has this problem?  Could it be a bad kernel?  A failing disk?  Anything?

Two boots ago I added a new repository and installed new software.  This software is still present, even though this particular boot it happened to revert back to the old startup entry.  Usually if I see the wrong wallpaper I just reboot and get the right one on the second try, but not always.  This is seriously getting annoying...

---

### Post by chargersfan420 on 2011-05-06
It is happening again!
I am now on 11.04 64-bit, using kernel 2.6.38-8-generic.  All of my partitions are now ext3.
I don't know if I have explained my situation well enough so perhaps this visual aid will help:

```

      Fresh install
            |
          /   \
        /       \ 
      /           \
    /               \
  /                   \
/                       \
-downloaded a file
-changed my theme
-set up compiz animations
                        -downloaded file has disappeared
                        -animation and theme changes are gone
-suddenly everything is back again
                        -suddenly everything is gone again

```

It seems my install has "forked" somehow, and every time I boot up, I get one of two "sessions".  Any changes I make to one session are gone whenever it randomly gives me the other session.  I can't seem to find any traces of two sessions in my home folder, and not sure where else to look.

Has anyone ever heard of anything like this?  It is really confusing and impossible to google.  It also concerns me very much that a file could suddenly disappear so easily.

---

### Post by chargersfan420 on 2011-05-06
Bump!

Please help!  I'm starting to think my hard drive is possessed or something...

---

### Post by chargersfan420 on 2011-10-26
Okay, I figured out what happened.

I've long been in the practice of having two 15 GB partitions (used for / ) and two 30 GB partitions (used for /home ).  Every time a new Ubuntu comes out I install to the pair of partitions I'm not using at the time.  I recently started to use gparted to copy my /home partition from one block to the other before starting a new install.  The problem with that is the UUID of the partition gets copied too, and because grub now uses UUID's, it wasn't sure which partition it was supposed to mount as home.  Sometimes it would mount one, and sometimes the other.

There are two things I can do to get around this (I chose to do both):
1.  Change the UUID of one of the partitions:
tune2fs -U random /dev/sda7
(where /dev/sda7 would be replaced with the partition in question)
2.  Change fstab to use /dev listings instead of UUID's.

---

