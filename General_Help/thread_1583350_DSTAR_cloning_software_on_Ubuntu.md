---
title: "DSTAR cloning software on Ubuntu"
date: 2010-09-27
forum: General Help
---

### Post by tkoco on 2010-09-27
I had the opportunity to program a new ID-880H DSTAR radio using ICOM's available cloning software. This software is Windows based. So thus, I had a mission to get this software running on Ubuntu with WINE.

Equipment:
ICOM DSTAR ID-880H radio
ICOM OPC-1529R cloning cable
Serial to USB converter
Laptop running 10.04 LTS Ubuntu (with WINE installed)
And an USB A to A extender cable

I downloaded the CS-80/880 cloning software from the ICOM website (go here [HTML]http://www.icom.co.jp/world/support/download/firm/IC-80AD_E_ID-880H_E/1_00/index.html[/HTML] or google "ICOM CS-80/880"). The file came as a "ZIP" file. I unzipped and installed the software.

After cabling up the OPC-1529R, USB converter, and the USB extension between the radio and the laptop, the software said "go - no" on the serial port!

I searched the forum for serial ports under WINE. They all indicated that a link was needed. Ok, I added the link (blindly) and tried again. Still a no-go.

So, I did a ```
ls -l ~/.wine/dosdevices
```
Lo and behold, the link was dead. Hummm.

Further searches on Google turned up a blog article about adding USB serial devices to WINE. [HTML]http://blog.mypapit.net/2008/05/how-to-use-usb-serial-port-converter-in-ubuntu.html[/HTML] Without rehashing the entire article, one good point the author made was to check if Ubuntu sees the USB converter. Sure enough, there was no additional USB device for the converter. After swapping things around, I discovered the USB extension cable was too long for the job. So, a shorter cable was substituted and the USB device now showed with the command "lsusb".

Back to the cloning program and WINE, I still could not get the program to see the serial port. A quick look at /dev directory revealed that the device name was different from the forum postings:
```
ln -s /dev/ttyUSB ~/.wine/dosdevices/com1
```
The correct link to create (for 10.04 LTS) is:
```
ln -s /dev/ttyUSB0 ~/.wine/dosdevices/com1
```

But, that trick still did not fix the serial port issue for me. So, further searching turned up a report on adding some definitions to the "~/.wine/system.reg" file.[HTML] http://wiki.jswindle.com/index.php/Wine_Registry#Serial_Com_Port[/HTML]
I edited the "~/.wine/system.reg" file and added the following to the end of the file:
```
[Hardware\\Devicemap\\Serialcomm] 1231984861 @="" 
"Serial0"="COM1" 
"Serial1"="COM2" 
"Serial2"="COM3" 
"Serial3"="COM4" 
"Serial4"="COM5" 
"Serial5"="COM6" 
"Serial6"="COM7" 
"Serial7"="COM8" 
"Serial8"="COM9" 
```

After restarting the cloning program, success. The serial port was visible and the program could read the internal memory of the radio.

Ahh, but this tale is not over yet!

 I had no problem reading the information from the radio, but when I attempted to update the radio (write the data), a "Cloning Error" stopped me cold. So, I did more investigation. CS-80/880 software allows you to read from the radio in either "normal" or "high" speed. But the radio will only accept data (writing data) in the "high" speed mode.
The other item is one of permissions in Ubuntu. I looked at the permissions of /dev/ttyUSB0. The group is set to "uucp". So I added myself the that group. That may be over-kill, but better safe than pulling one's hair out.

Good Luck!

---

### Post by spmitchell3 on 2010-11-09
I don't know anything about editing files or programming for that matter.  How do I edit wine to add what you did?

---

### Post by tkoco on 2010-11-16
> **spmitchell3 said:**
> I don't know anything about editing files or programming for that matter.  How do I edit wine to add what you did?
Relatively easy. Open a terminal window (Applications -> Accessories -> Terminal). Go to the wine directory ```
$ cd .wine
``` and edit the file like this:```
 $ gedit system.reg
``` In gedit, move the cursor to the end of the file (down arrow and right arrow keys) and press Enter. 
At your web browser, click and drag over the code to select it with the mouse. Press the Control & C keys together to copy the code. 
Move the mouse from the web browser to the gedit window. Now press Control & V keys together to paste the code. 
The code should copy over to the gedit window. Then in gedit, click on "Save" and then exit.

---

