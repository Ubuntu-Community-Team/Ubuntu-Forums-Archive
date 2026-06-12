---
title: "Efax error since 10.04 upgrade"
date: 2010-05-03
forum: General Help
---

### Post by graven80 on 2010-05-03
Since upgrading a couple of days ago to 10.04, I've noticed my fax program (Efax) has stopped working and gives the following error messages when trying to send a fax:-

[B]Error: can't read multi-strip TIFF files

Error: missing offset to TIFF data[/B]

Prior to upgrade, Efax was working perfectly with my serial modem. This error arises even though I'm trying to send a postscript file as I always have previously.

Is this a known bug?, or has anyone any ideas on how to overcome this? I'd welcome any help.

Thanks

---

### Post by graven80 on 2010-05-03
Just a little further info. The files I'm trying to fax are definitely OK (ie: not corrupted in any way) as I can send them via efax from Ubuntu 9.10 on a different drive in the same pc.

---

### Post by jssilva on 2010-05-04
Same here on Ubuntu 10.04 final release.
jss

---

### Post by graven80 on 2010-05-09
I've now managed to find a fix for this problem. There's a newer version of efax-gtk available as a .tgz file (version 3.2.1 by Chris Vine ). Either compile from source, or if you prefer, you can add ppa:eugenesan/ppa to your software repository and upgrade from the package manager. 

I used the latter method and it's worked perfectly.

---

### Post by ms4 on 2010-05-09
Hello,

I proposed  [cce ]("http://www.cce.com/sent.html")to add -dMaxStripSize=0  in file /usr/bin/fax at line

$GS -q -sDEVICE=tiffg3 -r$RES  -dNOPAUSE -dSAFER \
resulting in

$GS -q -sDEVICE=tiffg3  -r$RES -dNOPAUSE -dSAFER -dMaxStripSize=0 \
best regards ms4

---

### Post by colin63a on 2010-05-24
This isn't strictly on the point but when I tried to fax using efax it said the document wasn't a valid postscript file - any thoughts please?

---

### Post by GlisGlis on 2010-06-08
I did: add ppa:eugenesan/ppa to my software repository and upgrade from the package manager. version 3.2.1 by Chris Vine, but it's not working.
Errors:
efax-0.9a: opened /dev/ttyS1
efax-0.9a: failed page /home/henk/Desktop/fax.ps.001
efax-0.9a: error: tcgetattr on fd=7 failed: Input/output error
efax-0.9a: error: fax device write: Input/output error
efax-0.9a: error: tcgetattr on fd=7 failed: Input/output error
efax-0.9a: error: fax device write: Input/output error
efax-0.9a: sync: dropping DTR
same 4 lines again
sync: sending escapes
same errors again.

I don know what to do. Could you give me a hand?

Henk

---

### Post by GlisGlis on 2010-06-08
[SOLVED]With wvdialconf /etc/wvdial.conf I found my modemport /dev/ttyACM0.
I changed the settings/modem/serial device in ttyACM0 and the modem works fine..

Henk

---

### Post by Scunizi on 2010-06-23
With Eugene's PPA (or most recent .deb) loaded I found that I had to change the modem initialization string to get the modem to work correctly. The following shows the stock initialization string and the changes I made to get my US Robotics USB modem to function.

Stock String and Changes:

Z &F0 - command to load generic template (doesn't work) - 
       changed &F0 to &F1 which loads the hardware flow control template

M1L0 - sets speaker ON until connect with LOW volume
       changed to M0L0 for speaker always OFF.  the usb modem doesn't have a speaker.

The first command change is what made it functional.  The modem default is designed for the windows environment where you're loading up the driver and software that controls the modem.  The change forces hardware control which is needed in Linux.  I tested on a 15 page fax and got some EOF errors at the end of several pages but when I looked at the fax all was normal.

Best advice... google the command set for your modem and see if you need to make some changes as well.

---

### Post by rolfp on 2010-07-27
> **ms4 said:**
> Hello,

I proposed  [cce ]("http://www.cce.com/sent.html")to add -dMaxStripSize=0  in file /usr/bin/fax at line

$GS -q -sDEVICE=tiffg3 -r$RES  -dNOPAUSE -dSAFER \
resulting in

$GS -q -sDEVICE=tiffg3  -r$RES -dNOPAUSE -dSAFER -dMaxStripSize=0 \
best regards ms4

Hi,
I dropped in here from google, running into this sort of error, also, on Mandriva 2010.1:
```
/usr/bin/efax: Tue Jul 27 16:27:24 2010 efax v 0.9a-001114 Copyright 1999 Ed Casas
efax: 27:24 Error: can't read multi-strip TIFF files
efax: 27:24 Error: missing offset to TIFF data
efax: 27:24 done, returning 2 (unrecoverable error)
```

Next, I tried what was in the stable release for gtk-efax but got similar results:
```
Socket running on port 9900
efax-0.9a: 16:46:51 Error: can't read multi-strip TIFF files
efax-0.9a: 16:46:51 Error: missing offset to TIFF data
efax-0.9a: 16:46:51 finished - unrecoverable error
Closing the socket

```

Then, I did your edit to the efax script, ms4.  All five pages went out, each showing a warning:

efax: 59:19 Warning: EOF before RTC

yet,
```
efax: 02:04 done, returning 0 (success)
```

All five tiff files created by modified fax display complete.  No feedback from the other end, yet, but just wanted to say, THANKS! :) How did you know that?
Rolf

---

### Post by blackhawx on 2010-08-13
i'm having the same trouble and trying to apply 
-dMaxStripSize=0

to the problem

but there is no user/bin/fax on my ubuntu system

did yo mean home/mysusername/bin...?

there is no bin folder for me unless i'm misinterpreting the source file.


please help

---

### Post by spipe on 2010-09-01
> **blackhawx said:**
> but there is no user/bin/fax on my ubuntu system

did yo mean home/mysusername/bin...?


Not user/bin/fax, but /usr/bin/fax is what you want.  If you have either the efax or efax-gtk package installed, /usr/bin/fax should be there.

I too want to thank ms4 for posting the workaround. Saved me some hair-tearing at work today.

---

### Post by RogerDavis on 2010-09-09
I got the following:
Error: can't read multi-strip TIFF files
Error: missing offset to TIFF data
finished - unrecoverable error

Maybe it's time to update efax in the Software Center, it's ancient!

---

### Post by Offoffoff on 2010-11-01
I have the same problem... Even after I put 
```
gs -q -sDEVICE=$FNTFMT -r204x196 -g${pelwidth}x$4 -dMaxStripSize=0 \
```
into /usr/bin/fax

---

### Post by Wolf-Ekkehard on 2010-11-03
ms4's fix sounded right on!  Alas, it didn't work for me :-(  I first fixed the parameters to $GS as instructed, and when it didn't work, I put some "printouts" (to files) into /usr/bin/fax to see when it got called and with what parameters.  I found out that /usr/bin/fax NEVER got called by efax-gtk.  Something else must have created the multi-strip tiff file (also probably using gs) that the darn thing can't read.

Is there any other script that does the job of fax?  I did a "which fax" and only got /usr/bin/fax.

Any other ideas out there?

---

### Post by Wolf-Ekkehard on 2010-11-04
For those of us who see no effect from changing the /usr/bin/fax script, the somewhat more elaborate fix that graven80 suggested seems to work just fine.  I got rid of my packages efax and efax-gtk, and did
```
sudo add-apt-repository ppa:eugenesan/ppa
sudo apt-get update
sudo apt-get install efax-gtk
```
and everything worked fine from there on.  BTW, the script /usr/bin/fax is gone now...

---

### Post by aguilla1 on 2011-01-27
I edited usr/bin/fax as directed, but still received the same error.
I then added the repository to obtain the update for E-Fax-gtk but received the following error:

E: /var/cache/apt/archives/efax-gtk_3.2.5-1~eugenesan~lucid2_i386.deb: trying to overwrite '/usr/share/man/man1/efax.1.gz', which is also in package efax 1 

Any ideas?

---

### Post by aguilla1 on 2011-01-27
I removed the existing packages (as instructed before) and now e-fax is running.

---

### Post by ericsonp on 2011-04-04
Neither the /usr/bin/fax mod, nor the eugenesan ppa solution appears to work for 10.04 patched up through today.

As pointed out earlier, /usr/bin/fax doesn't appear to be getting called. Or at least I can delete it and still get the same error.

Attempting to install the eugenesan ppa solution I get:

```
dpkg: error processing /var/cache/apt/archives/efax_1%3a0.9a-19_amd64.deb (--unpack):
 trying to overwrite '/usr/share/man/man1/efix.1.gz', which is also in package efax-gtk 0:3.2.5-1~eugenesan~lucid
```2

-Paul

---

### Post by mosaic2s on 2011-04-06
> **Wolf-Ekkehard said:**
> For those of us who see no effect from changing the /usr/bin/fax script, the somewhat more elaborate fix that graven80 suggested seems to work just fine.  I got rid of my packages efax and efax-gtk, and did
```
sudo add-apt-repository ppa:eugenesan/ppa
sudo apt-get update
sudo apt-get install efax-gtk
```and everything worked fine from there on.  BTW, the script /usr/bin/fax is gone now...

did that. works fine now.
using D-LINK DFM-560E MODEM.

---

