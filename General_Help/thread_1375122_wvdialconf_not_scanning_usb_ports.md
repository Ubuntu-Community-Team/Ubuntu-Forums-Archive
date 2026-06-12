---
title: "wvdialconf not scanning usb ports"
date: 2010-01-07
forum: General Help
---

### Post by Silvertones on 2010-01-07
Well I'm trying to set up a US robotics dial up USB Modem. When I enter WVDIALCONF
I end up with a screen that says "scanning your serial ports for a modem"
It scans and ends up saying Sorry'no modem was detected!Did you configure it properly with SETSERIAL?

It appears it's not scanning the USB ports.
Any ideas?

---

### Post by Silvertones on 2010-01-07
If I run lsusb it shows.
I also installed it in Windows to be certain the device works and it does. If I can't get this thing working I'm gonna have to give up on Ubuntu and don't want to do that.
PLEASE HELP!!!!!!!!!:(

---

### Post by Silvertones on 2010-01-07
john@ubuntu:~$ dmesg
  
  [  149.192070] usb 1-1: new full speed USB device using uhci_hcd and address 3
  
  [  149.360927] usb 1-1: configuration #1 chosen from 1 choice
  
  [  149.859257] cdc_acm 1-1:1.0: ttyACM0: USB ACM device
  
  [  149.862438] usbcore: registered new interface driver cdc_acm
  
  [  149.862453] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
  
  john@ubuntu:~$ 



    john@ubuntu:~$ ls /dev/ttyu* /dev/ttya* /dev/ttyh*
  
  ls: cannot access /dev/ttyu*: No such file or directory
  
  ls: cannot access /dev/ttya*: No such file or directory


    john@ubuntu:~$ wvdialconf
    Editing `/etc/wvdial.conf'.
     
   
  Scanning your serial ports for a modem.
     
   
  ttyS0<Info>: Device or resource busy
    Modem Port Scan<*1>: S0   S1   S2   S3   
    ttyACM0<Info>: Device or resource busy
    Modem Port Scan<*1>: ACM0 
     
   
   
   
  Sorry, no modem was detected!  Is it in use by another program?
    Did you configure it properly with setserial?
     
   
  Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)
     
   
  If you still have problems, send mail to <wvdial-list@lists.
  
  ls: cannot access /dev/ttyh*: No such file or directory
  
  john@ubuntu:~$

---

### Post by alexfish on 2010-01-07
hi

Which version of Ubuntu are you using

thanks in advance

---

### Post by Silvertones on 2010-01-08
I'm using 9.1

Thanks

   john@ubuntu:~$ sudo wvdial /etc/wvdial.conf
  --> WvDial: Internet dialer version 1.60
  --> Warning: section [Dialer /etc/wvdial.conf] does not exist in wvdial.conf.
  --> Cannot get information for serial port.
  --> Initializing modem.
  --> Sending: ATZ
  --> Sending: ATQ0
  --> Re-Sending: ATZ
  --> Modem not responding.
  john@ubuntu:~$

---

### Post by alexfish on 2010-01-08
hi

this guide here may help:

[SIZE=2][COLOR=Blue][Connections to card using wvdial (gnome-ppp is a front end to wvdial making it largely redundant) ]("http://www.pcurtis.com/ubuntu-mobile.htm#wvdial")[/COLOR][/SIZE]


Also look here

			 			[Ubuntu 9.10 mobile broadband can't connect]("http://ubuntuforums.org/showthread.php?t=1331660") 			([IMG]http://ubuntuforums.org/images/misc/multipage.gif[/IMG]  [1]("http://ubuntuforums.org/showthread.php?t=1331660") [2]("http://ubuntuforums.org/showthread.php?t=1331660&page=2"))

regards alex fish

---

### Post by Silvertones on 2010-01-08
This is a US Robotics USB dial up modem. It got great reviews for use with Ubuntu. Using Gnome-ppp when I press the button to get the info, forgot the exat label, is says "no Modem detected".

What is the meaning of this message:
Warning: section [Dialer /etc/wvdial.conf] does not exist in  wvdial.conf.

My wvdial.conf file is located in Filesystem/etc/wvdial.conf
The file is in the etc folder. Is this right?

This is how it reads:

[Dialer Defaults]
Auto DNS = yes
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 48800
New PPPD = yes
Stupid mode = yes
;carrier check = no
Modem = /dev/ttyACM0
ISDN = 0
Phone = 4460568
Password = mypassword
Username = myusername

---

### Post by Silvertones on 2010-01-08
[http://ubuntuforums.org/showthread.php?t=1375907](http://ubuntuforums.org/showthread.php?t=1375907)

---

### Post by alexfish on 2010-01-09
hi

special drivers for linux required... 
[http://linmodems.org/](http://linmodems.org/)

[http://ubuntuforums.org/showthread.php?t=728384](http://ubuntuforums.org/showthread.php?t=728384)

[http://www.linuxforums.org/articles/how-to-connect-a-dial-up-modem-in-ubuntu-9_509.html](http://www.linuxforums.org/articles/how-to-connect-a-dial-up-modem-in-ubuntu-9_509.html)

looking for more will post here since this is first thread

---

### Post by unixbhaskar on 2010-01-09
what "lsusb" print? Can u pls post that?

Plus I think your modem pointing to wrong port....

---

### Post by Silvertones on 2010-01-09
To both thanks. I've posted the results of sudo wvdial. It tries but fails. I've read all of the articles Alexfish. The reviews  for this USB modem were 95% possitive with Ubuntu.



It was suggested I move the thread here:

[http://ubuntuforums.org/showthread.php?t=1375907](http://ubuntuforums.org/showthread.php?t=1375907)

---

