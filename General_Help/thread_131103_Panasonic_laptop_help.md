---
title: "Panasonic laptop help"
date: 2006-02-15
forum: General Help
---

### Post by Derktoon on 2006-02-15
anyone know of any specific problems with the panasonic CF-45DJ series? The basic specs are 

P2 - 266
96 mb RAM
4gb Hard drive (some of them have 8 though)
and i assume it has a propriotary panasonic mother board

the reason being i attempted to install kubuntu last night on one of them and it gave me an error saying something like (and ill get the exact wording down later tonight when i try again) "method execution error" and it let me continue on from there, but it just hung untill i forced it off. I did let it sit there for a ridiculous amount of time before killing it. Anyone have any clues? My first thought is that maybe the system wasnt up to spec and perhaps needed more RAM or a larger hard drive...but i dont know. :-k :-?

---

### Post by Derktoon on 2006-02-16
mkay, im sitting here at the laptop and the message is:

"the debootstrap program exited with an error (return value 1)
check /target/var/log/bootstrap.log for the details."

SO, there you have the exact wording, and i really need some quick help on this one...i have to do this 25 times for 25 diffrent computers which im selling for $80...so, the sooner i get an answer the sooner i get some cash (which i really really can use) ^_^ thanks again for simply being here to look at my problems!

---

### Post by SivArt on 2006-02-16
Did you tried to disable all the BIOS functions before the installation (video, NIC, parallel port, USB, etc...). Or check if the clockrate and the latency are matching your processors settings.

---

### Post by SivArt on 2006-02-16
[quote=SivArt]Did you tried to disable all the BIOS functions before the installation (video, NIC, parallel port, USB, etc...). Or check if the clockrate and the latency are matching your processors settings.[/quote] 
Also, do you have teh model number so I can check it out!!! :KS

---

### Post by Derktoon on 2006-02-16
ok, well the modle number is a panasonic CF-45...and i think i found the problem...i ran a verification on the CD-rom i burned and it seems to be failing on the ./pool/main/p/parted/libparted1.6-12_1.6.21-1ubuntu3_i386.deb file... ^_^

---

### Post by SivArt on 2006-02-17
Well, It is great to know that you have a possible workaround for this problem. Also, I want to advice you to download the image file again and verify it with the any md5 checksum software (it is going to tell you if the image file is okay before burning it :)). Please let me know if the new image resolved your problem.

Thank you!!!

Also, here are the download links
For kubuntu: [http://us.releases.ubuntu.com/releases/kubuntu/breezy/]("http://us.releases.ubuntu.com/releases/kubuntu/breezy/")
For ubuntu: [http://mirror.mcs.anl.gov/pub/ubuntu-iso/5.10/]("http://mirror.mcs.anl.gov/pub/ubuntu-iso/5.10/")

Unfortunately, you cannot request free disks for kubuntu, but if you need some, you can buy them at: [http://www.kubuntu.org/shops.php]("http://www.kubuntu.org/shops.php")

And you can always request free disks of ubuntu on our homepage:KS

I am going to check the model number and if I found something helpful, I will let you know!!!

---

### Post by Derktoon on 2006-02-17
sweet, im downloading a new copy of the ISO from bittorrent. unfortunately im on my work line so its gonna take some time...anyway, how do i run the MD5 check to see if everything is there? remember im fairly new to all of this. thanks for doing research for me though ^_^ that will help a lot!

---

### Post by SivArt on 2006-02-20
[FONT=Arial][SIZE=2][FONT=&quot]First, you need to download the image file and compare it with the MD5 checksums that ubuntu have provided, you can use any of the freeware MD5 checkers on the web the result of the MD5 checker must match exactly with the ones that ubuntu homepage has provided.[/FONT][/SIZE][/FONT]
   [FONT=Arial][SIZE=2][FONT=&quot]You can download the MD5 checksums file and the MD5 checker. The MD5 checker is easy to use (it is not a big deal); the procedure is quite simple, you must compare the MD5 checksum result with the one that ubuntu has provided you.[/FONT][/SIZE][/FONT]
   
   [FONT=Arial][SIZE=2][FONT=&quot]The MD5 checksum file for ubuntu 5.10:  [http://mirror.mcs.anl.gov/pub/ubuntu-iso/5.10/MD5SUMS]("http://mirror.mcs.anl.gov/pub/ubuntu-iso/5.10/MD5SUMS")[/FONT][/SIZE][/FONT]
   [FONT=Arial][SIZE=2][FONT=&quot]The MD5 checksum file for kubuntu 5.10: [http://us.releases.ubuntu.com/releases/kubuntu/breezy/MD5SUMS]("http://us.releases.ubuntu.com/releases/kubuntu/breezy/MD5SUMS")[/FONT][/SIZE][/FONT]
   
   [FONT=Arial][SIZE=2][FONT=&quot]This is one of the MD5 checker engine, you can use anyone, there are a lot of them on the web: [http://md5deep.sourceforge.net/]("http://md5deep.sourceforge.net/")[/FONT][/SIZE][/FONT]
   [FONT=Arial][SIZE=2][FONT=&quot]
[/FONT][/SIZE][/FONT]> 
   [FONT=Arial][SIZE=2][FONT=&quot]:KS First, uncompress the zip file in the location that you have the image file.[/FONT][/SIZE][/FONT]
   [FONT=Arial][SIZE=2][FONT=&quot]:KS Second, issue the "MD5deep -e *image_file_name*".[/FONT][/SIZE][/FONT]
   [FONT=Arial][SIZE=2][FONT=&quot]:KS Wait until the MD5 checker finished and compare the results.
:KS At that point and if the results match, you can safely burn the ISO file.
[/FONT][/SIZE][/FONT] 
 [FONT=Arial][SIZE=2][FONT=&quot]
[/FONT][/SIZE][/FONT]=D>[FONT=Arial][SIZE=2][FONT=&quot] If you need further help please let me know.[/FONT][/SIZE][/FONT]

---

### Post by Derktoon on 2006-02-20
actually i just re-downloaded the ISO and tried it again and everything works like a dream...well, a slow dream, this is only a 266 im working on. but dang, this is really slick!!

---

### Post by SivArt on 2006-02-20
Well, It is great to know that the problem has been resolved; you can make the money that you need :). If you need some additional assistance please let me know. Also, please remember to test the whole system before selling those (Just to be sure that everything is working fine). Also, if you need a good office package try openOffice.
> [FONT=Verdana]OpenOffice download link: [http://download.openoffice.org/2.0.1/]("http://download.openoffice.org/2.0.1/")[/FONT][FONT=Arial]
[/FONT][FONT=Verdana][SIZE=2]It was a pleasure assisting you with this issue.
[/SIZE][/FONT][FONT=Verdana][SIZE=2]
:KS bye, bye...[/SIZE][/FONT]

---

### Post by y23 on 2007-09-29
Yep, I've got a Panasonic CF-45, too.

Great to hear got it working.   Did the PCMCIA work as well?

I got other Linux's working fine, but **the PCMCIA is not working** We get a dreaded ANONYMOUS MEMORY error and that's the same with all distros we tried.

I heard a lot of good things about Ubuntu, and I wonder if it gets the PCMCIA to work, or if its a problem unrelated to the distro.

And then, should I try Ubuntu 5.10 or would 7.04  work, too?

We want to make the old laptop into  a console-only LAN-only  LAMP server.
Is this illusory with 96mB RAM?  It works fine with knoppix on even slower/lessRAM machines.

I have decided to try 
  Ubuntu 6.06 LTS - Supported to 2011
 alternate desktop CD with ** text-based installer**.

Is that a good idea?

So many unknown unknowns ;-)

My current PCMCIA error messages  is here:
[http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?;act=ST;f=8;t=19160](http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?;act=ST;f=8;t=19160)
DMESG here [http://y23stockpic.free.fr/misc/panasonic_notebook.html](http://y23stockpic.free.fr/misc/panasonic_notebook.html)

[PHP]0000:00:0a.0 CardBus bridge: Texas Instruments PCI1250 (rev 02)
cs: warning: no high memory space available!
cs: unable to map card memory!
[/PHP]

NEW:  Puppy 2.17 (kernel 2.6.21.5)  

upon inserting XIRCOM RE-100 card ... DMESG says:  Detected deprecated PCMCIA ioctl usage from process: cardmgr.
and  **xirc2ps_cs: node-id not found in CIS**  

upon inserting XIRCOM CEM56-100 ..  the terminal freezes.  When I pull out the card it comes alive again.
DMESG says:
eth0: Xircom: port 0x310, irq 3 ...
pcmcia: registering new device pcmcia0.0
pcmcia: could not parse base and rmask0 of CIS
xirc2ps_cs: manfid not found in CIS

ho hum.

Here is someone who must have it running ...
[http://ubuntuforums.org/showthread.php?t=80423&page=11](http://ubuntuforums.org/showthread.php?t=80423&page=11)

---

