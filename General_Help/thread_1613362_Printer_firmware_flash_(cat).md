---
title: "Printer firmware flash (cat)"
date: 2010-11-04
forum: General Help
---

### Post by El Rifle on 2010-11-04
My problem is this:

I wanted to upgrade the firmware of my HP Business Inkjet 1200, with a HP tool on Windows, via USB. HP was not really clear about when starting up again etc, so now my printer is dead, only the flash-setting on the printer works (pushing 2 buttons at the same time). 
The HP tool doesn't recognize the printer anymore, so the tool has became useless. Ubuntu also doesn't recognize it automatically, so my conclusion is that it is really damaged.

1. A solution I found,  is to manually copy a firmware file to the printer with a DOS command, but only possible with a parallel connection **(which I don't have)** 
described here:```

http://forums13.itrc.hp.com/service/forums/questionanswer.do?admit=109447627+1288878863391+28353475&threadId=978234 Please follow the steps below : 

REQUIRES: Direct Parallel Connection (only) 

1.  Hold down the RESUME+CANCEL buttons while powering on the printer. The  printer will enter into reflash mode. The POWER and RESUME LEDs will be  turned ON. 

2. Select Start->Run. 

3. In the Run box, type "CMD" and press ENTER. This will bring up a DOS shell window. 

4.  If needed, change to the directory containing the MMR2020W.FMW file.  For example, if the FMW file is located in a folder called  "C:\TEMP\1200FW\", type CD \TEMP\1200FW and press ENTER. The prompt  should change to indicate the current directory. If the directory is  located on a different drive letter, type CD D: and press ENTER to  change to the other drive, where D should be replaced with the  appropriate drive letter. Then change to the correct directory. 

5.  Type the following command to start the firmware transfer: COPY /B  MMR2020W.FMW LPT1: and press ENTER. This will start the firmware  transfer. LPT1 can be replaced if using a different parallel port (e.g.  LPT2, LPT3, etc.) 

6. Wait for 30 seconds for flashing to start.. 

7.  If, after flashing, the printer does not power-up on its own, manually  power-on the printer. (Hold the power button for a few seconds) 

WARNING:  DO NOT CLOSE THE DOS WINDOW until the flashing is complete and the  printer powers off (and possibly back on). Closing the window too soon  could interfere with the flash process and prevent the printer from  working properly. Once flashing has completed, type EXIT and press ENTER  to close the DOS window.
```2. I think that it is possible via Ubuntu, (why not) and via USB (if the tool could upgrade it through USB, it should work). I found a site from another type of HP printer where it described how to do it: ```
[http://www.openprinting.org/printer/hp/hp-laserjet_1020](http://www.openprinting.org/printer/hp/hp-laserjet_1020)
      The firmware of the printer must be uploaded after turning it on.
You can use a hotplug/udev script which comes with foo2zjs, or do it manually:

**"cat /usr/share/foo2zjs/firmware/sihp1020.dl >     /dev/usb/lp0"**.
```The problem is, that I think that because the firmware is damaged, **the computer doesn't recognize the printer, so I don't know where to send the firmware to. I can't find any 'lp0' either.**


3. This is the outcome of my lsusb
```

lsusb
Bus 008 Device 002: ID 05fe:1011 Chic Technology Corp. 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```The first one is my mouse, the printer is connected to bus 006

[B]Who can help me with a code or some other kind of help. The printer is in flash mode as I said before, with the 2 lights on the printer on at the same time.



[/B]

---

