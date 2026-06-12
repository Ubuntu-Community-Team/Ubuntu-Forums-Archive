---
title: "smartctl"
date: 2011-01-22
forum: General Help
---

### Post by darkcoffee on 2011-01-22
How am I suppose to check the health of my HDD?  Because I used 'smartctl -H /dev/sda' and it did not work.  I want to know if the HDD is dying or not.

---

### Post by MooPi on 2011-01-22
Possibly try the gui for smartcontrol,  > gsmartcontrol
I use this on a bootable flash for diagnostic purposes.

---

### Post by Alan.Brown on 2011-01-22
Using Ubuntu 10.10.  Try System > Administration > Disk Utility.   It will allow you to view SMART data and run diagnostic tests an each Hard Disk you have

Mine are both failing :( 

Alan

---

### Post by darkcoffee on 2011-01-22
There is no GUI.  I am trying to check this on a Ubuntu server.

---

### Post by matt_symes on 2011-01-22
Hi

Did you try it with root permissions ?

```
sudo smartctl -H /dev/sda
```

On my laptop returns

```
matthew@matthew-laptop:~$ sudo smartctl -H /dev/sda
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

matthew@matthew-laptop:~$ 
```

Kind regards

---

### Post by darkcoffee on 2011-01-22
> === START OF READ SMART DATA SECTION === SMART overall-health self-assessment test result: PASSED  That too is what I got.  But the test was like 1 second.  So I was skeptical that it actually scanned.  Seriously, is this really it?

---

### Post by switch10 on 2011-01-22
> **darkcoffee said:**
> That too is what I got.  But the test was like 1 second.  So I was skeptical that it actually scanned.  Seriously, is this really it?

Yes.  SMART data is stored on your HDD.  smartmontools is just reading it.  There is no testing required.  

If you want a more detailed output, try the -A option instead of -H.

---

### Post by Don Barzini on 2011-01-22
> **darkcoffee said:**
> How am I suppose to check the health of my HDD?  Because I used 'smartctl -H /dev/sda' and it did not work.  I want to know if the HDD is dying or not.

To check the statistics run.....

```
sudo smartctl -a /dev/sda
```

That will give you the stats and info of the drive.

To run a short test type.....

```
sudo smartctl -t short /dev/sda
```

The test will tell you when it will stop and therefore be alright to run another **smartctl -a**. It's usually 5 or 10 minutes (I can't remember exactly).

If you want to save the output of the drive's stats to a text file, run....

```
sudo smartctl -a /dev/sda > /directory/filename.txt
```

Check **man smartctl** in a terminal window for more info.

---

