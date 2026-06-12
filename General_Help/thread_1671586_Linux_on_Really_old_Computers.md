---
title: "Linux on Really old Computers"
date: 2011-01-20
forum: General Help
---

### Post by NativeAngels on 2011-01-20
I have a really ancient Toshiba Satalite Pro 480cdt with pcmcia wirless card with pcmcia card and would like to install linux on it. Its pretty low spec and i dont have a eithernet card for it. Any help welcomed.

---

### Post by Vigh on 2011-01-20
Xubuntu

or Ubuntu with the really really light-weight GUI display manager Lxde I think its called

---

### Post by lithopsian on 2011-01-20
Pentium 233?  Probably 64MB of memory or less?  How much disk space?  You won't get Ubuntu on it.  Maybe one of the really lightweight distros.  Maybe only command line.  I imagine the battery is shot?  If it has more memory than that then maybe a cut-down Ubuntu.  The CPU is always going to be slow with X server running, you'll want a very lightweight desktop like Openbox with no bells and whistles.

Does it have a CD?  Probably not.  You can install from flash drives, or any storage that you can boot from really, if you have another machine to create the installation.

You don't need an ethernet card if it has wireless.  It is possible to install Linux over a network from another machine but this isn't the way I'd try in this case unless there were no other options.

---

### Post by Sylos on 2011-01-20
Puppy linux might be your best bet. I managed to get that running on a laptop with only 64mb RAM. 

I doubt youll get anything Ubuntu flavoured running in GUI with less than 256mb RAM. Even Lubuntu struggles at that.

---

### Post by mastablasta on 2011-01-20
DSL - it's old kernel and software but will support the hardware probably.

---

### Post by Hippytaff on 2011-01-20
[Slitaz]("http://www.slitaz.org/en/get/") is good for older laptops, you'd need access to the internet from another pc, which you obviously have because you posted here, and right the iso to liveCD/USB.

---

### Post by cascade9 on 2011-01-20
> **lithopsian said:**
> Pentium 233?  Probably 64MB of memory or less?  How much disk space?  You won't get Ubuntu on it.  Maybe one of the really lightweight distros.  Maybe only command line.  I imagine the battery is shot?  If it has more memory than that then maybe a cut-down Ubuntu.  The CPU is always going to be slow with X server running, you'll want a very lightweight desktop like Openbox with no bells and whistles.

Does it have a CD?  Probably not.  You can install from flash drives, or any storage that you can boot from really, if you have another machine to create the installation.

You don't need an ethernet card if it has wireless.  It is possible to install Linux over a network from another machine but this isn't the way I'd try in this case unless there were no other options.

Unless its got an upgrade is 233MMX, 32-64MB, 3.8GB HDD, CD rom. 

There would be a USB port, but installing from USB 1.0/1.1 would be..lets just say, grab a copy of 'war and peace' to read duing the installation process. 

That old system could probably run some linux distro, but it would only be for fun and giggles IMO.

---

### Post by ronnielsen1 on 2011-01-20
[http://lightlinux.blogspot.com/2008/06/top-10-of-lightweight-linux_24.html](http://lightlinux.blogspot.com/2008/06/top-10-of-lightweight-linux_24.html)

Knowing how much memory you have would be nice.

> DSL recommends a P200 and 64 MB. 
Puppy should run on any Pentium with at least 32 MB


---

### Post by Hippytaff on 2011-01-20
[This is worth a look]("http://kmandla.wordpress.com/hardware/"). Old laptops are much more useful than some would have you think, and you don't need x.org!

---

### Post by NativeAngels on 2011-01-20
Hello Yes it does have a cdrom drive and woo a external floppy drive i assume its got 64mb memory. I have tried slackware 10.0 which installs. older dsl with 2.4 kernal. Will kernal 2.6 work on this laptop. I have a buffalo, trendnet and belkin wireless card. Its it possible to use pcmcia wireless with a server edition of ubuntu ?

---

