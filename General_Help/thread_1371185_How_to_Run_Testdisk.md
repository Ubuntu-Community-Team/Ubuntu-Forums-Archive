---
title: "How to Run Testdisk"
date: 2010-01-03
forum: General Help
---

### Post by Mukoi on 2010-01-03
Hi,
I'm new to Ubuntu and linux.
I've altered the partition on my hard drive. Won't boot into windows. Do not have internet. Heard that testdisk should help. I have downloaded some testdisk files to a usb flash drive via another computer.
 
Have ubuntu 9.10 DVD, so can use this.
 
Step by step, how do I get testdisk to work?

---

### Post by atjesse on 2010-01-03
> **Mukoi said:**
>  
Step by step, how do I get testdisk to work?

See [http://www.cgsecurity.org/wiki/TestDisk#Documentation](http://www.cgsecurity.org/wiki/TestDisk#Documentation)

---

### Post by Mukoi on 2010-01-03
> **atjesse said:**
> See [http://www.cgsecurity.org/wiki/TestDisk#Documentation](http://www.cgsecurity.org/wiki/TestDisk#Documentation)
 
Thank you.  My problem is that I can't get testdisk to run.

---

### Post by amsterdamharu on 2010-01-03
"Won't boot into windows. "

There are lots of reasons it won't boot from messing up the entire partition with the data on it to moving it to another partition so the boot.ini has wrong info.

First figure out if this can be solved by simply recover the mbr or change the boot.ini (post the error you get while booting)

When you install testdisk do you get any errors? When you run it do you get any errors?

As for testdisk you can get it here:
[http://packages.ubuntu.com/karmic/testdisk](http://packages.ubuntu.com/karmic/testdisk)

You might have a dependency problem since one package might need another and so on and your computer is not connected to the Internet therefor cannot retrieve the packages automatically. You can try to install it and see what packages are missing.

---

### Post by Mukoi on 2010-01-03
> **amsterdamharu said:**
> "Won't boot into windows. "
 
There are lots of reasons it won't boot from messing up the entire partition with the data on it to moving it to another partition so the boot.ini has wrong info.
 
First figure out if this can be solved by simply recover the mbr or change the boot.ini (post the error you get while booting)
 
When you install testdisk do you get any errors? When you run it do you get any errors?
 
How do I install and run testdisk?

---

### Post by amsterdamharu on 2010-01-03
What's the error you get when trying to boot windows?

As for testdisk you can get it here:
[http://packages.ubuntu.com/karmic/testdisk](http://packages.ubuntu.com/karmic/testdisk)
(download links are at the bottom of the page)
Probably this package:
[http://packages.ubuntu.com/karmic/i386/testdisk/download](http://packages.ubuntu.com/karmic/i386/testdisk/download)

You might have a dependency problem since one package might need another and so on and your computer is not connected to the Internet therefor cannot retrieve the packages automatically. You can try to install it and see what packages are missing.

In ubuntu just double click on the deb file.

---

### Post by Leppie on 2010-01-03
> **Mukoi said:**
> How do I install and run testdisk?

to install testdisk:
```
$sudo apt-get install testdisk
```
or go to System>Administration>Synaptic, enter testdisk in the searchbox, select to install and apply.

to run testdisk:
```
$sudo testdisk
```

---

### Post by Mukoi on 2010-01-03
> **Leppie said:**
> to install testdisk:
```
$sudo apt-get install testdisk
```
or go to System>Administration>Synaptic, enter testdisk in the searchbox, select to install and apply.
 
to run testdisk:
```
$sudo testdisk
```
 
Unfortunately, that didn't work.
 
Thank you.
 
I have just downloaded the ".deb" file that the other person suggested.  Will see how that goes.

---

### Post by Mukoi on 2010-01-03
> **amsterdamharu said:**
> What's the error you get when trying to boot windows?
 
As for testdisk you can get it here:
[http://packages.ubuntu.com/karmic/testdisk](http://packages.ubuntu.com/karmic/testdisk)
(download links are at the bottom of the page)
Probably this package:
[http://packages.ubuntu.com/karmic/i386/testdisk/download](http://packages.ubuntu.com/karmic/i386/testdisk/download)
 
You might have a dependency problem since one package might need another and so on and your computer is not connected to the Internet therefor cannot retrieve the packages automatically. You can try to install it and see what packages are missing.
 
In ubuntu just double click on the deb file.
 
It worked.  Thanks.
Unfortunately, it seems that I have lost my data.  Fortunately, I have a backup that is a few days old - prior to my problem.  I will reinstall that and redo the work that I lost.  I have spent days and days trying to solve this problem.  Hardly any sleep.
I have learnt from the experience.
Thanks to you and the others for their help.

---

### Post by bety on 2011-08-17
hi, i got the same problem. all my partition was format and lost everything.i used to have windows 7 OS, then i changed it to ubuntu 10.04 and that laptop doesn't connect to internet. i klik the link that you provided but it's error.
how should i get the proper link to get the software and the dependency problem. 
it happen yesterday, made my day so bad i couldn't even slept well.

thank you very much for your help

regards 

Bety

---

### Post by dandnsmith on 2011-08-18
I suggest [using Hirens BootCD](http://www.hiren.info/pages/bootcd), so you can boot it directly, and run testdisk from that.

---

