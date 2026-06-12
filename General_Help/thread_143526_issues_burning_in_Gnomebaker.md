---
title: "issues burning in Gnomebaker"
date: 2006-03-12
forum: General Help
---

### Post by warbux on 2006-03-12
I am having a lot of issues burning Cd-r's and Cd-rw's  in Gnomebaker..here is the following code

```
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
cdrecord: Permission denied. Cannot open '/dev/sg0'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 3 = CD-ROM XA mode 2
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord: 
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .

```

---

### Post by njzillest on 2006-03-12
use something different 

if you want to burn music try x-cd roast or serpintine audio creator 


im sure theres a DVD burner somewhere in synaptic just look around :)

---

### Post by taurus on 2006-03-12
You can always try k3b for burning CDs & DVDs...

---

### Post by warbux on 2006-03-12
i get errors with all those programs.  is it possible the burner is not supported?

---

### Post by taurus on 2006-03-12
Do you mean you get the same error message when you try to burn with k3b?  Do kind of burner do you have anyway?

---

### Post by OBnascar on 2006-03-12
I also today just happened to get the same exact error you posted, I have an external CD-RW, DVD-RW and I first thought that it was broken when I booted into Nero in WinXP and it would not burn there either.

With ubuntu I used Gnomebaker and K3d both and also tried it with K3b in Kubuntu on a different computer. When it would not burn there either then I had realized I was using the same CD-RW disk all the time.

This may not be your problem but I threw that disk in the trash, put in a different one and my problem was gone. That should have been the first thing I had checked, but that would have been to easy, right ?..........................lol

---

### Post by warbux on 2006-03-15
i have a PHilips CD-RW, i cant find the exact model name.

---

### Post by Egmontman on 2006-03-18
I am totally new at this whole Linux thing. I did have the same problem as you. I amended the gnomebaker short cut with "gksudo" before it. It works fine now. I had guessed that that "permission denied" thing was something to do with that. Again, i could be totally out to lunch. I have only been using Linux for 2 weeks now.
Cheers

---

### Post by vignesh on 2006-03-18
I use GnomeBaker too.. I am able to write CD-RW`s but unable to write onto any normal cds .

---

### Post by sprinkles on 2006-03-18
[QUOTE=vignesh]I use GnomeBaker too.. I am able to write CD-RW`s but unable to write onto any normal cds .[/QUOTE]
I will have no idea how to help you either way, but you might get a better response if you include the full error message you're getting when you try and burn to CDRs

---

### Post by jerrykenny on 2006-03-18
I've seen a similar thing with k3b, and it an updated version of cdrecord (or sometimes cdrdao) which was only abailable to the root user . . . 

If thats the case, . . . . then you'll be able to do anything if you launch gnomebaker (or k3b) from a terminal with the command 

sudo gnomebaker

the burning programme will then be running with root privelidges

a long term solution then is to update the permissions on the offending executable file.

---

