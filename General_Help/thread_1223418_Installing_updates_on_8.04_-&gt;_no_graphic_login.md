---
title: "Installing updates on 8.04 -&gt; no graphic login"
date: 2009-07-26
forum: General Help
---

### Post by VadimRadionov on 2009-07-26
Hello,
  
 Yesterday i installed some proposed packages updates on 8.04 and today,  trying to boot, the graphic login prompt fails to load.  Everything starts as  usual, the logo appears and the progress bar grows, then switches to text mode  (lat line saying: "Running local boot scripts (/etc/rc.local) [OK]").  Then it  tries to switch to graphics mode, but nothing appears and soon it falls back to  text.  This happens a couple of times.
  
 Then the blue text screen appear saying: "The display serves has been shut down about 6 times in the last 90 seconds.   It is likely that something bad is going on.  Waiting for 2 minutes before  trying again on display :0"
  
 How can it be fixed?
  
 Thanks you in advance,
  
 Vadim

---

### Post by miegiel on 2009-07-26
Possibly your */etc/X11/xorg.conf* has been replaced during the update by one that doesn't work with your monitor. With a little luck your old */etc/X11/xorg.conf* has been backed up.

To be safe start by backing up your current */etc/X11/xorg.conf* (requires root/superuser privileges).
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.2009.07.26
```

To list *xorg.conf* files by modification date including backups (oldest file first).
```
ls -ltr /etc/X11/xorg.*
```

See if you can find any differences between the more recent backups and your current *xorg.conf*.

To view a file (in text mode).
```
cat /etc/X11/xorg.conf
```

To edit your */etc/X11/xorg.conf* (requires root/superuser privileges)
```
sudo nano /etc/X11/xorg.conf
```

---

