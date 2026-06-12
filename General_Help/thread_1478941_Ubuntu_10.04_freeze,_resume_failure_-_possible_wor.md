---
title: "Ubuntu 10.04 freeze, resume failure - possible workaround"
date: 2010-05-10
forum: General Help
---

### Post by StuartN on 2010-05-10
If anyone has an Ubuntu 10.04 installation that suddenly freezes while working, or fails to resume from suspension, and the freeze / resume failure is not due to the i8xx or memory leakage issue, perhaps you could try these (entirely safe) workaround steps:

1. In ~.xsession-errors you may see *"(firefox-bin:3097): Gdk-WARNING **: XID collision, trouble ahead"* and other errors. Change your screensaver to "Pictures folder". This follows advice in http://ubuntuforums.org/showthread.php?t=1474730"

2. In ~/.xsession-errors you may see *"Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory Please ask your system administrator to enable user sharing."* Enable sharing by sharing a directory and following the installation prompts. You can remove the share once the Samba components have been installed.

My machine _seems_ to be behaving over multiple resumes since making these changes. My notes on this problem are at [http://www.iol.ie/~stuartneilson/Bootup_fsck.html](http://www.iol.ie/~stuartneilson/Bootup_fsck.html)



The memory leak issue and an Intel i8xx problem are described here:

X/Bugs/Lucidi8xxFreezes - X freezes (GPU lockups) are being experienced on i845, i855 and other 8xx chips.
We experimented with several different settings but could not find a combination which resolved all issues for all 8xx owners. Below are some of the settings that can be changed if the combination we picked for the release did not work for you. [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

X/Testing/GEMLeak: GEM memory leak from GLX 1.3/1.4 backport - Recently in Lucid, a major memory leak was found in the X.org server which causes the computer to get slower and slower over time. This is reported as bug 565981. This does not affect cards using proprietary drivers or not using DRI2 because it is specific to the glx module that the open drivers use. Intel will always be affected since DRI2 is used with and without KMS, ATI uses DRI1 without KMS. [https://wiki.ubuntu.com/X/Testing/GEMLeak](https://wiki.ubuntu.com/X/Testing/GEMLeak)

---

### Post by StuartN on 2010-05-10
> **StuartN said:**
> My machine _seems_ to be behaving over multiple resumes since making these changes. My notes on this problem are at [http://www.iol.ie/~stuartneilson/Bootup_fsck.html](http://www.iol.ie/~stuartneilson/Bootup_fsck.html)

My machine froze again, and could only be rebooted with REISUB - the same errors in demsg:

```
[    2.644522] EXT4-fs (sda4): INFO: recovery required on readonly filesystem
[    4.066338] EXT4-fs (sda4): orphan cleanup on readonly fs
```

I notice also that there is yet another missing directory, ~/.config/metacity does not exist, in .xsession-errors:

```
Window manager warning: Failed to read saved session file /home/stuart/.config/metacity/sessions/10ce4223c261411605127350520720563800000012500026.ms: Failed to open file '/home/stuart/.config/metacity/sessions/10ce4223c261411605127350520720563800000012500026.ms': No such file or directory
```

---

