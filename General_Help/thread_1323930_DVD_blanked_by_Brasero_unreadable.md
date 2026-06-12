---
title: "DVD blanked by Brasero unreadable"
date: 2009-11-12
forum: General Help
---

### Post by zensys on 2009-11-12
On 9.10 (but if I recall well with previous versions as well) and on two different notebooks/DVD-drives I have the following problem:

Each time I blank a (previously mountable/readable) DVD with Brasero (but also with dvd+rw-format) Brasero ends with succesfully blanked disc but the disc is unreadable afterwards. Sometimes the disc keeps spinning and reboot or manual eject is the only solution. Mounting results in:

```
timmo@HM:~$ sudo mount -l /dev/sr0
[sudo] password for timmo: 
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

timmo@HM:~$ 

```

and then dmesg:

```
[  150.490334] UDF-fs: No anchor found
[  150.490343] UDF-fs: No partition found (1)
[  150.708113] ISOFS: Unable to identify CD-ROM format.
[  190.937066] CE: hpet increasing min_delta_ns to 22500 nsec
[ 1344.008920] UDF-fs: No anchor found
[ 1344.008929] UDF-fs: No partition found (1)
[ 1344.159764] ISOFS: Unable to identify CD-ROM format.
timmo@HM:~$ 
```

I searched extensively for solutions but though many users have similar problems, solutions are rare or at least did not work for me.

A normal blank, unused dvd does mount and the Brasero-blanked DVD's aren't readable in Windows either ('disc might be damaged').

Help is very much needed and appreciated!!

cheers,
Timmo

---

### Post by Mark Phelps on 2009-11-12
Don't use Brasero, long-time fan of K3b.  Should try using that instead.

---

### Post by philinux on 2009-11-12
I seem to remember reading that blanking is not good anyway better to overwrite.

I did find this info to recover ones that got borked.
```
Try this to blank problem dvd
growisofs -Z /dev/dvd=/dev/zero

Then this with or without lead-out
dvd+rw-format -force -lead-out /dev/dvd

and this to change the format of the disk to UDF
mkudffs /dev/dvd
http://mindspill.net/computing/linux-notes/how-to-format-a-dvd-with-udf.html
```

---

### Post by zensys on 2009-11-12
Mark, thanks for the tip. I installed K3b and it works! I read about it but thought it would just be another gui to the same tools and also I was reluctant to install a KDE application but that is probably unnecessary purist.

Phil, your lines seem to work as well though I am not sure, as after the formatting I was not able to mount (but apparently Nautilus does not mount blank dvd's though on the other hand blank dvd fresh from the spindle do mount).

The UDF formatting went well. I read somewhere that depending on the UDF version incompatibility problems might arise with (windows based) players. Is there a way to check the UDF version of a disk? And if necessary is there also a command to format with iso9660?

Thanks a lot guys, I will sleep better!

cheers, Timmo

---

### Post by desgua on 2010-03-12
philinux

Thank you so much! I've been trying to fix my second broken dvd (by brasero) and now it works.

I'm very happy. :D

---

### Post by Sylchat on 2010-09-16
I got the same problem and the command line format worked...
dvd+rw-format -force -lead-out /dev/dvd2
It seems that the growisofs does the same thing.

Also, is the lead-out necesary knowing that it would be done when burning data (lead-out is used to finish the dvd and prevent firther writings on the dvd).

However I don't understand why Brasero would make dvd unwritable after a blank???

There is a bug here:
[https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/495144](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/495144)
but no news since Dec 2009 :(

---

### Post by nyolo on 2010-10-23
> **philinux said:**
> I seem to remember reading that blanking is not good anyway better to overwrite.

I did find this info to recover ones that got borked.
Try this to blank problem dvd
```
growisofs -Z /dev/dvd=/dev/zero
```

Then this with or without lead-out
```
dvd+rw-format -force -lead-out /dev/dvd
```

and this to change the format of the disk to UDF
```
mkudffs /dev/dvd
```
[http://mindspill.net/computing/linux-notes/how-to-format-a-dvd-with-udf.html]("mindspill.net/computing/linux-notes/how-to-format-a-dvd-with-udf.html")

When I run the first instruction, I obtain the following return:

```
:-( /dev/dvdrw: media is not recognized as recordable DVD: 0
```
I checked with a eject/eject-t that dvd tray is on /dev/dvdrw, also tried growisofs with /dev/dvd and /dev/scd0.

Any help with this issue?

PS: I expect not to bother for retagging original message. It's just for easing reading.

---

