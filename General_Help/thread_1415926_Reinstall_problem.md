---
title: "Reinstall problem"
date: 2010-02-25
forum: General Help
---

### Post by Namesake on 2010-02-25
Hey all,

I have a problem. I currently have a dell laptop xps m1330 with a 250 GB hardrive. I am running 9.10, which was upgraded from 9.04.

I am keen to do a full reinstall of 9.10 not just an upgrade. 
The problem is, I have a bunch of files I want to keep, but I do not have an external HDD to back up the files. I  currently have 83GB free on my on board HDD. I want to save about 70GB.

Can I partition my HDD, shift the files, reformat and install on the original portion then clear the the partition?

Another little hurdle, instead of burning the Ubuntu install software to dvd, can I do it with a 4Gb usb stick instead?


Thanks in advance!

:D

---

### Post by MelDJ on 2010-02-25
70GB is very big. i think you will need around 15 dvds to burn all the files into it.
why not upgrade in this situation? it seems the best option

---

### Post by Namesake on 2010-02-25
I think you got me wrong, I want to shift all the files I want to keep onto onto the 70Gb partition, then I want to wipe the remaining 180Gb and reinstall Ubuntu 9.10 onto it. Is this possible?

---

### Post by MelDJ on 2010-02-25
yes you can. 
just make sure you dont format it when your are installing ubuntu again

---

### Post by Namesake on 2010-02-25
How do I go about partitioning my HDD?

---

### Post by Namesake on 2010-02-25
Also,

can I make a boot disc on a usb?

---

### Post by MelDJ on 2010-02-25
> **Namesake said:**
> How do I go about partitioning my HDD?

is ubuntu the only os on the drive?

> **Namesake said:**
> Also,

can I make a boot disc on a usb?

yes. see: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by Namesake on 2010-02-25
Yeah Ubuntu is the only OS,

Thanks for the link, will check now

---

### Post by oldfred on 2010-02-25
You can keep the new partition as a data partition and mount that in your new install. I had updated in place for 3 years and only had root and swap. With a new drive I had lots of room so I moved /home, but also moved all data to /data. Where all data was all the folders in /home.
I then installed to another partition as I thought I may want an old setting somewhere but only found 1 or 2 minor issues that I could have recreated without much difficulty. My new /home ended up less than 1GB with all my data in the data partition. Next time I will keep home inside rooot (backed up) and just keep /data separate.

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
Partitioning basics with some info on /data
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)

---

### Post by Namesake on 2010-02-25
> **oldfred said:**
> You can keep the new partition as a data partition and mount that in your new install. I had updated in place for 3 years and only had root and swap. With a new drive I had lots of room so I moved /home, but also moved all data to /data. Where all data was all the folders in /home.
I then installed to another partition as I thought I may want an old setting somewhere but only found 1 or 2 minor issues that I could have recreated without much difficulty. My new /home ended up less than 1GB with all my data in the data partition. Next time I will keep home inside rooot (backed up) and just keep /data separate.

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
Partitioning basics with some info on /data
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)

Wow, thanks for all the links and advice, I will follow it up shortly - as for now, I am still struggling with the USB boot disk.

 As stated earlier, I am using UNetbootin. I followed the instructions, and when I reboot I choose to boot from the USB. It displays the UNetbootin splash screen with only one option - default - to choose from. It counts down from 10 seconds. And then just repeats the count down... no live Ubuntu start up.

If I choose to edit the default option, I am given this
```

>/ubnkern initrd=/ubninit

```What's going on here? Well confused

---

### Post by Namesake on 2010-02-27
Okay, I gave in. I bought an external HDD to make it all easier.

What would be the best way to set up my file system such that maintenance is easy.

Thoughts?

---

### Post by MelDJ on 2010-03-01
stuff pendrive + external hard drive + windows partition with your files

---

