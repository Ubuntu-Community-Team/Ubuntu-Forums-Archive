---
title: "Garmin eTrex Vista H connection issues"
date: 2011-04-10
forum: General Help
---

### Post by waldzinator on 2011-04-10
Hello,

I've read through several previous posts on this (both in Ubuntu Forums and some Bugzilla reports under Fedora).  I'm currently running Ubuntu Maverick - 2.6.32-30-generic.  I recently bought a Garmin eTrex Vista H, which connects via usb (from my reading, it looks like older versions connected over serial).  Well, like so many before me, I can't seem to write to or read from the device via gpsbabel.

Originally tried to read anything from the device (I have one waypoint in there) via: ```
gpsbabel -i garmin -f usb:
```  It returned "Found no Garmin USB devices."  I then tried turning on the eTrex.  Doing the same while locating satellites just does nothing - I have to escape from the command in terminal.  Trying again produces the error: 
> Claim interfaced failed: could not claim interface 0: Device or resource busy.

After doing some research, I unblacklisted and then reblacklisted garmin_gps.  I also went into ```
/etc/udev/rules.d/51-garmin.rules
``` to verify that the contents were: > SYSFS{idVendor}=="091e", SYSFS{idProduct}=="0003",         MODE="666", as directed in [this]("http://www.gpsbabel.org/os/Linux_Hotplug.html") .  Everything seemed to be correct.

I then followed some other advice found [here]("https://bugzilla.redhat.com/show_bug.cgi?id=485554") and created the policy under /etc/hal/...
Still no luck!

Does anybody have any ideas?????  As you can see, I did my research and can't come up with it!

---

### Post by meijer.o on 2011-04-10
Start gpsbabel as root and it will work

---

### Post by waldzinator on 2011-04-10
No dice.  Interestingly, I hooked up my Garmin Forerunner 305 (sports watch) and ran ```
sudo gpsbabel -i garmin -f usb:-1
``` which subsequently returned device information > 0 3409562826 484 Forerunner305 Software Version 2.80
.  So, the problem appears to be isolated to the eTrex Vista H.

Other thoughts?

---

### Post by 5149.5 on 2011-04-10
Is the Vista in the correct mode? I think I remember two modes. One was for NMEA and the other was for talking to PC, RS232 maybe?

---

### Post by waldzinator on 2011-04-10
I took a look at the settings on the Garmin, and this is not an option.  I was under the impression that NMEA only worked over serial, though, so that might be why.  This might be overkill, but I ran gpsbabel in Debug mode...here's the output:

```
sudo gpsbabel -D9 -i garmin -f usb:
GPSBabel Version: 1.3.6 
TX [12]:00 00 00 00 05 00 00 00 00 00 00 00 ............(SESREQ  )
TX [12]:00 00 00 00 05 00 00 00 00 00 00 00 ............(SESREQ  )
TX [12]:00 00 00 00 05 00 00 00 00 00 00 00 ............(SESREQ  )
RX (intr) [16]:00 00 00 00 06 00 00 00 04 00 00 00 e1 5d 63 e3 ..............c.(ACK     )
TX [12]:14 00 00 00 fe 00 00 00 00 00 00 00 ............(PRDREQ  )
RX (intr) [16]:00 00 00 00 06 00 00 00 04 00 00 00 e1 5d 63 e3 ..............c.(ACK     )
RX (intr) [12]:00 00 00 00 02 00 00 00 00 00 00 00 ............(REQBLK  )
RX (bulk) [113]:14 00 00 00 ff 00 00 00 65 00 00 00 bd 03 04 01 65 54 72 65 78 20 56 69 73 74 61 20 48 20 53 6f 66 74 77 61 72 65 20 56 65 72 73 69 6f 6e 20 32 2e 36 30 00 56 45 52 42 4d 41 50 20 41 4d 52 20 53 74 61 6e 64 61 72 64 20 41 75 74 6f 72 6f 75 74 65 20 42 61 73 65 6d 61 70 2c 20 4e 52 20 33 2e 30 30 00 56 45 52 53 4d 41 50 20 4e 6f 6e 65 00 ........e.......eTrex.Vista.H.Software.Version.2.60.VERBMAP.AMR.Standard.Autoroute.Basemap..NR.3.00.VERSMAP.None.(PRDDAT  )
RX (bulk) [50]:14 00 00 00 f8 00 00 00 26 00 00 00 56 45 52 47 50 52 4f 4d 20 4e 6f 6e 65 00 47 50 53 20 42 72 61 76 6f 33 20 56 65 72 73 69 6f 6e 20 32 2e 31 33 00 ............VERGPROM.None.GPS.Bravo3.Version.2.13.(PRDEDA  )
RX (bulk) [144]:14 00 00 00 fd 00 00 00 84 00 00 00 50 00 00 4c 01 00 41 0a 00 54 01 00 41 64 00 44 6e 00 41 c9 00 44 ca 00 44 6e 00 44 d2 00 41 2d 01 44 38 01 44 2e 01 41 90 01 44 6e 00 41 f4 01 44 f5 01 41 58 02 44 58 02 41 59 02 44 59 02 41 bc 02 44 bc 02 41 20 03 44 20 03 41 21 03 44 21 03 41 84 03 41 86 03 41 87 03 41 88 03 41 89 03 44 84 03 41 8b 03 44 8b 03 44 8c 03 44 8d 03 44 8e 03 41 8c 03 44 8f 03 41 92 03 41 94 03 41 96 03 44 96 03 ............P..L..A..T..Ad.Dn.A..D..Dn.D..A..D8.D..A..Dn.A..D..AX.DX.AY.DY.A..D..A..D..A..D..A..A..A..A..A..D..A..D..D..D..D..A..D..A..A..A..D..(PRTARR  )
TX [12]:00 00 00 00 05 00 00 00 00 00 00 00 ............(SESREQ  )
RX (intr) [16]:00 00 00 00 06 00 00 00 04 00 00 00 e1 5d 63 e3 ..............c.(ACK     )
TX [12]:14 00 00 00 fe 00 00 00 00 00 00 00 ............(PRDREQ  )
RX (intr) [12]:00 00 00 00 02 00 00 00 00 00 00 00 ............(REQBLK  )
RX (bulk) [0]:(RET2INTR)
RX (intr) [-110]:(REQBLK  )
TX [12]:14 00 00 00 fe 00 00 00 00 00 00 00 ............(PRDREQ  )
RX (intr) [-110]:(CMDDAT  Abort)
Unit:    
ID:    0
Version:    0.00RX (intr) [-110]:(CMDDAT  Abort)
RX (intr) [-110]:(CMDDAT  Abort)
RX (intr) [-110]:(CMDDAT  Abort)

```

The whole Rx (intr) [-110] thing keeps going on and on.  So, from the output, it looks like there *is* device recognition.  Seeing this problem, I did some more digging and found this [bug]("http://sourceforge.net/mailarchive/forum.php?thread_name=AANLkTi%3D8OZL7%3D5%2Bw-yVesnr5M8Z2MZyJCE6i4hPtC%3Dm9%40mail.gmail.com&forum_name=gpsbabel-misc").  Not sure where this leaves me...

---

### Post by waldzinator on 2011-04-13
Problem solved.  Posted message to gpsbabel maiilng list.  Turns out I was running an old version...Synaptic, however, wasn't showing this to couldn't apt-get upgrade.  Ended up deleting old version and compiling newest from CVS.  Works great!

---

