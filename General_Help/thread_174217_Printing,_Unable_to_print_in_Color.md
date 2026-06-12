---
title: "Printing, Unable to print in Color"
date: 2006-05-11
forum: General Help
---

### Post by cgprint on 2006-05-11
I have tried for some time on various linux systems to print in color to a Phaser 850 (postscript), most recently Dapper 6.06 full patchs, and 5.10 only getting a black n white output. (using the installer defaults for postscript driver)

The 850 is networked, going direct to the ip address, lp.  The test always comes out in Black n white.

I have taken the colorcir.ps and converted it to a pdf and printed it from WinMe, Through a CentOS 4.3 box, running LPR, and it prints in color. works directly to the printer too. Printing directly from this box via linux = BW.

Any Ideas. 

Thanks

---

### Post by OMRebel on 2006-05-11
Have you tried using TurboPrint?  Give the evaluation copy a shot and see if it'll print in color using their driver.

---

### Post by cgprint on 2006-05-11
Turboprint does not show that as a supported printer

---

### Post by jcornuz on 2006-05-11
Hi,

I have been using Dapper / Breezy for a while without problems on an HP 7660 and Canon S 450 but since the last updates on Dapper I can only get B & W too.

I hope it is related to the update of CUPS and will get sorted with the next update....

Take care.

Joel

____________________________________

                [jcornuz.awardspace.com]("http://jcornuz.awardspace.com")

---

### Post by OMRebel on 2006-05-11
Doh!  I should have looked at their printer list before I suggested it.  Sorry about that.  I know I was able to print to a Phaser 560 (yikes! what a dinosaur!) in color before with Breezy.

Looking at Linuxprinting.org, it should work fine:
[http://www.linuxprinting.org/show_printer.cgi?recnum=Tektronix-Phaser_850](http://www.linuxprinting.org/show_printer.cgi?recnum=Tektronix-Phaser_850)

I'm not real sure what to try to be honest.  Hopefully someone here will be able to tell ya how to fix the problem.

---

### Post by cgprint on 2006-05-11
I turned on debug in /etc/cups.conf and found this tidbit. I did and apt-get install on hpijs and hplip and it said it was up to date. this is on 6.06 updated very latests. 

no other clues in the logs, still prints in BW only.


May 11 16:20:52 ubuntu hp: unable to open /var/run/hplip/hpssd.port: No such file or directory: prnt/hpijs/hplip_api.c 94 

May 11 16:20:52 ubuntu hp: unable to connect hpssd socket 50002: Connection refused: prnt/hpijs/hplip_api.c 720

---

