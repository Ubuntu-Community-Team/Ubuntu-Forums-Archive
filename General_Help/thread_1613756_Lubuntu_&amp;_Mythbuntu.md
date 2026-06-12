---
title: "Lubuntu &amp; Mythbuntu?"
date: 2010-11-04
forum: General Help
---

### Post by Yezinki on 2010-11-04
How do I install Lubuntu & Mythbuntu in Ubuntu?

Thanks.

---

### Post by WorMzy on 2010-11-04
```
sudo apt-get install mythbuntu-desktop lubuntu-desktop
```

(lubuntu available from Karmic Koala [9.10] onwards, mythbunutu from Hardy Heron [8.04])

---

### Post by thatguruguy on 2010-11-04
Do you really want both?  Mythbuntu has its own DE (specifically, Xubuntu).  Why not just install Lubuntu and then install the mythtv frontend and/or backend?

---

### Post by Yezinki on 2010-11-04
Thanks WorMzy & guruguy for your replies.

At the moment I have Ubuntu with KDE interface.

You mean to say that I can install Lubuntu in Ubuntu but Myth I gotto install as a separate new install?

Regards!

---

### Post by thatguruguy on 2010-11-04
No.

You can install the MythTV frontend and/or backend on Lubuntu. Or Ubuntu. Or Kubuntu. Or OpenSuse. Or whatever.

Mythbuntu is a full OS, with a (somewhat stripped-down) Xubuntu as its DE.  Just install the Lubuntu desktop, remove the Kubuntu desktop, and install the MythTV backend and/or frontend.

For instance, I have a Mythbuntu box hooked up to my TV. I also have the MythTV frontend on both my computer and my kids' computer, both of which have a regular Ubuntu install, so that live TV can be streamed to those computers.

---

### Post by Yezinki on 2010-11-05
My machine crashed when I installed Lubuntu....it already had Kubuntu installed in Ubuntu but when I added Lubuntu it froze.

Thanks.

---

### Post by WorMzy on 2010-11-05
Installing packages should not cause Ubuntu to crash. I suspect you have a problem with your hardware.

---

### Post by Yezinki on 2010-11-05
WorMzy you are correct....was able to get into Lubuntu & probably at some setting about system > HDD > it displayed a message after running some HDD tests, high temp > the machine needs to be serviced coz of dust & 12 bad sectors.

May be coz installed a lot of softwares never restarted & the machine is on 24/7 not even a reboot.

Than I formatted Ubuntu with K & Lubuntu & installed Ubuntu only.

How does one perform a CHLDSK in Linux?

Regards!

---

### Post by WorMzy on 2010-11-05
CHKDSK is a Windows Utility for fixing problems with a Windows partition. The equivalent for Linux is [fsck]("http://manpages.ubuntu.com/manpages/maverick/en/man8/fsck.8.html"); I'm not sure that this will help though. Sounds like your PC just needs a bit of a clean. :)

If you want to run fsck anyway, then just open a terminal and run:
```
sudo shutdown -rF now
```

This will restart your PC, and Ubuntu will run fsck on your root partition while it's booting up.

---

### Post by Yezinki on 2010-11-05
Thanks for the info WorMzy I know CHKDSK is a windows utility & meant whats it equivalent in Linux.

Regards!

---

### Post by Yezinki on 2010-11-05
WorMzy it was quick..........can I view its results someway?

---

### Post by WorMzy on 2010-11-05
Possibly. Open a terminal and run:
```
sudo cat /var/log/fsck/checkroot
```

If nothing shows up, then the log file is empty. If you boot into a LiveCD, you can run fsck manually on your root partition (you can't run it while the partition is mounted), but if the check went quickly, then it's safe to assume that fsck found no problems on the partition.

---

### Post by Yezinki on 2010-11-05
" Nothing has been logged yet" is the output.

---

### Post by Yezinki on 2010-11-05
very quick hardly 5-10 secs.

---

### Post by WorMzy on 2010-11-05
Like I said, you can boot into a LiveCD and manually run fsck if you want to. Just makes sure that you don't mount the partition before you run fsck on it.

Once you've booted into the LiveCD (or USB) just open a terminal and run (assuming your root partition is sda1 and is formatted as ext4):

```
fsck.ext4 -fpc /dev/sda1
```

---

