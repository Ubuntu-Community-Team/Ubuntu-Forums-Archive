---
title: "ubuntu 12.04 and arduino uno"
date: 2012-10-01
forum: General Help
---

### Post by firebug on 2012-10-01
I have had this thing working on 12.04 before which is what is so confusing to me about this.  I followed this tutorial

[http://www.pluggy.me.uk/arduino-ubuntu/](http://www.pluggy.me.uk/arduino-ubuntu/)

and it worked.  Well I guess that even though I have been using Ubuntu since version 6.10 I still only have enough knowledge about the programming end to call myself a newbie.  Needless to say I ran my install through the ropes a few times and was ready for a fresh install (this happens more than it probably should for me).  After the new install I ran updates then followed the tutorial again word for word.  This time when I open the Arduino IDE go to the tools section the serial port selection is now greyed out and the only use that I can get out of my UNO is plug it in and I have one expensive blue led that lights up on my desk since I cannot connect to it I cannot program it.  I have tried everything that I can find online including installing all these java programs

 java-common, openjdk-6&7, java-wrappers, libjaxme-java, default-jre, defaul-jdk, libbsf-java, default-jre-headless, openjdk-6-jre-headless

still no serial port I have seen the fix by soldering a 10k resistor on the back of the board but I don't think that mine is the older version since I have had it working on 12.04 before.  I can't locate a serial number on the board as I did not order it from Arduino but a cheaper version off of ebay.  It looks just like the UNO's I see online except it does not have the actual Arduino logo (infinite sign with a - in one loop and a + in the other) but still has Arduino UNO and the Arduino website printed on it.   I cannot locate the UNO with either dmesg or lsusb.  any help would be greatly appreciated.  I will post the output of dmesg in a file as it is extremely long.  I even tried running dmesg both with the Arduino plugged in and without it plugged in then saved the output of each into a separate file then ran the diff command with both files and got nowhere there either but I do not think it worked right the output of that was 

> [    0.187072] pci 0000:03:00.0: BAR 6: assigned [mem 0x91420000-0x9142ffff pref]
> [    0.187075] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
382,383d383
< basstard@IOI:~$ [   10.913469] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
< bash: syntax error near unexpected token `)'

---

