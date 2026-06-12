---
title: "Help needed in configuring N73 for gprs"
date: 2010-01-19
forum: General Help
---

### Post by anikondemand on 2010-01-19
Help needed in configuring N73 for gprs. Is there any application available or how can I configure it manually?
 
Pls help.

---

### Post by anikondemand on 2010-01-19
Help:(.

---

### Post by DannStarr on 2010-01-19
What do you mean exactly? you want to connect to laptop / PC to tether? 

Do you currently have the internet working on your phone?

---

### Post by anikondemand on 2010-01-19
I want to connect my Nokia N73 to my laptop and access gprs through it. I am using ubuntu 8.04.

---

### Post by alexfish on 2010-01-19
hi

have you looked here

[https://help.ubuntu.com/community/PortableDevices/Nokia](https://help.ubuntu.com/community/PortableDevices/Nokia)

[http://cviorel.easyblog.ro/2008/11/05/nokia-n73-synchronization-with-opensync-under-ubuntu-804/comment-page-1/](http://cviorel.easyblog.ro/2008/11/05/nokia-n73-synchronization-with-opensync-under-ubuntu-804/comment-page-1/)

---

### Post by anikondemand on 2010-01-19
> **alexfish said:**
> hi

have you looked here

[https://help.ubuntu.com/community/PortableDevices/Nokia](https://help.ubuntu.com/community/PortableDevices/Nokia)

[http://cviorel.easyblog.ro/2008/11/05/nokia-n73-synchronization-with-opensync-under-ubuntu-804/comment-page-1/](http://cviorel.easyblog.ro/2008/11/05/nokia-n73-synchronization-with-opensync-under-ubuntu-804/comment-page-1/)

Thanks for the link. Will try it and post the result here.

---

### Post by anikondemand on 2010-01-19
Got the solution from somewhere else in this forum. Posting it here for future references.

> Connect your phone via datacable
open terminal & type 

lsusb

now u will get the following output

owais@owais-desktop:~$ lsusb
Bus 002 Device 001: ID 0000:0000 
Bus 001 Device 004: ID 0421:0445 Nokia Mobile Phones 
Bus 001 Device 002: ID 046d:092f Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000 
owais@owais-desktop:~$ 


it is on my compter,ur will not be exactly the same...

Now note the line in which NOkia Mobile Phones is written...it has two number one is 0421 & other is 0445...we'll take these numbers as 0x421 & 0x445

0421 is the Vendor ID & 0445 is the Product ID

Now enter this comand.

sudo /sbin/modprobe usbserial vendor=0x(vid) product=0x(pid)

eg, in my case::: sudo /sbin/modprobe usbserial vendor=0×421 product=0×445

Now enter this command

wvdialconf create
u'll get a long output which will be like 

Scanning your serial ports for a modem.
Port Scan: S0 S1 S2 S3
WvModem: Cannot get information for serial port.
ttyACM0: ATQ0 V1 E1 &#8212; OK
ttyACM0: ATQ0 V1 E1 Z &#8212; OK
ttyACM0: ATQ0 V1 E1 S0=0 &#8212; OK
ttyACM0: ATQ0 V1 E1 S0=0 &C1 &#8212; OK
ttyACM0: ATQ0 V1 E1 S0=0 &C1 &D2 &#8212; OK
ttyACM0: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 &#8212; OK
ttyACM0: Modem Identifier: ATI &#8212; Nokia
ttyACM0: Speed 4800: AT &#8212; OK
ttyACM0: Speed 9600: AT &#8212; OK
ttyACM0: Speed 19200: AT &#8212; OK
ttyACM0: Speed 38400: AT &#8212; OK
ttyACM0: Speed 57600: AT &#8212; OK
ttyACM0: Speed 115200: AT &#8212; OK
ttyACM0: Speed 230400: AT &#8212; OK
ttyACM0: Speed 460800: AT &#8212; OK
ttyACM0: Max speed is 460800; that should be safe.
ttyACM0: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 &#8212; OK
Found an USB modem on /dev/ttyACM0.
Modem configuration written to create.
ttyACM0: Speed 460800; init &#8220;ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0?

NOw.. notice the output says that there is a modem at /dev/ttyACM0 & max speed is 460800

now enter this command

sudo gedit /etc/wvdial.conf

A file will open in text editor...now delete everything in that file & paste the following there

[Dialer Defaults]
Modem = Your Modem Name(eg, /dev/ttyACM0 in my case)
Baud = ur max speed(460800 in my case)
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Phone = *99#
Username = username
Password = password
Stupid Mode = 1

save the file & you are done


NOw whenevr u need to connect...open terminal & type wvdial,,wait till some sort of IP adress is displayed like

pppd: ?[06][06][08]` [06][08]
primary DNS address 218.248.240.135
pppd: ?[06][06][08]` [06][08]
secondary DNS address 218.248.240.79
pppd: ?[06][06][08]` [06][08]

Now you are connected....hit cntrl+c to dissconnect...



U can also create a laucher on desktop(application in terminal) & keep the command as wvdial..now double click it & u r connected

Its working fine.
Thanks.

---

### Post by niceguy123 on 2010-01-19
Just tried anikondemand's advice but don't think that that has changed my situation for the better. 

Connected via USB cable, I see my cellphone listed under mobile broadband and can even connect and then see both wireless network and mobile broadband listed as connected. But, if I disconnect from the wireless or turn off the wireless modem and leave the mobile broadband connected I am not getting any connectivity in my browser. 

Internet works on the cellphone.

Can someone help me connect via my cellphone modem?

Thanks.

---

### Post by niceguy123 on 2010-01-19
I have just discovered that my computer has connected to the modem on my cellphone allowing use of skype. But am not able to surf the web on a browser.

The browser works on a wireless (or wired) dsl connection.

Can someone help with the needed configuration for the cell modem.

Thanks.

---

### Post by tlcstat on 2010-01-26
Greetings, I love you!!! It works!!! Motorola Quantico W845 using Ubuntu Karmic 9.10
Just one question?
Does anyone know the significance of this string that I get at logon

--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.

It doesn't keep me from connecting. Also this is a FYI the original readout had my modem speed at 9600 baud. I ignored that and put in the 460800 anyway and I have a very fast connection. I did turnoff my local wifi connection at the connection manager. At first I didn't think I had a connection because there was an X in the connection manager but when I opened Firefox I had internet. This makes sense sense since the tether is a USB and not a WIFI connecton.

This is just great. I have been trying for a week to get this new phone connected. Many thanks for your post.
tlcstat

Greetings, 
The solution in this thread by anikondemand works just great on my moto phone. It should be stickied, there are a lot of people searching for this solution. 
However, I did lock out my WIFI card by opening my phone while my WIFI was logged in. It also locked out my WVdial setup. Not sure of the exact sequence. I managed to unlock my card by booting from my original Karmic Install CD in Test mode and setting up my WIFI manually. When I rebooted back to my hard drive installation my WIFI was back but I had to set it up manually just like when on the CD. Wvdial setup came back when the WIFI went back up. This is just a heads up. I would avoid logging into the phone without the Wifi logged out [should say disconnected]. 
Tlcstat

Does anyone know the significance of this string that I get at logon

--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.

SOLVED needed to run wvdial as root
sudo wvdial

tlcstat

Greetings,
This tether solution works fine but I have been having a persistence problem. I reboot or go back to my wifi, then run the wvdialer it no longer finds my USB. It only scans the serial ports then reports no phone. The work around I am using is this script.
wvdial.sh
sudo modprobe usbserial vendor=0X22b8 product=0X2ca4
wvdialconf create
sudo wvdial

When I dial from this script my phone logs in every time. So, I'm good. 

However if there is something I need to change I would appreciate the feedback. 

This is a copy of my config file

[Dialer Defaults]

Modem = /dev/ttyUSB0
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Phone = #777 
Username = **********@uscc.com 
Password = **********
Stupid Mode = 1


This is a copy of the terminal text
[sudo] password for tlcstat: 
Editing `create'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0 S1 S2 S3 
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB0<*1>: Modem Identifier: ATI -- Manufacturer: I: Motorola CE, Copyright 2000
ttyUSB0<*1>: Speed 9600: AT -- OK
ttyUSB0<*1>: Max speed is 9600; that should be safe.
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
WvModem<*1>: Cannot get information for serial port.
ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.

Found a modem on /dev/ttyUSB0.
Modem configuration written to create.
ttyUSB0<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detected. Starting PPP immediately.
--> Starting pppd at Wed Jan 27 10:32:39 2010
--> Pid of pppd: 4129
--> Using interface ppp0
--> local IP address 166.223.1.11
--> remote IP address 166.181.191.1
--> primary DNS address 166.181.191.17
--> secondary DNS address 166.181.127.17

I use Ctrl+C to exit
Everything works fine except without the script I have no persistence.

thanks
tlcstat

---

### Post by alexfish on 2010-01-31
Hi

normally if things are working Then don't tamper

I don't know if the following will help

however adding permissions to the correct groups etc can help with dialout connections : Make backups and take note of changes you make, you may have to reverse your changes

All at you own risk:


The easiest way to get the required privileges is to do System -> Administration -> Users and Groups then unlock with your password and highlight your user name and click Properties and on the User Privileges Tab tick 'Connect to Internet using a Modem' which adds you to the dip group and 'Use Modems' which adds you to the dialout group. Neither act immediately and you need to restart or logout and back in as the same user.

If this does not work or you prefer to use a terminal then the following two commands will add YOURUSERNAME to the dip and dialup groups

sudo adduser YOURUSERNAME dip
sudo adduser YOURUSERNAME dialout

You can check which groups you are in (and get some other useful information by:

id


Permissions for /etc/ppp/pap-secrets and etc/ppp/chap-secrets

If you want to save the username and password in gnome-ppp they are saved in /etc/ppp/pap-secrets and etc/ppp/chap-secrets and you need to give read and write access to them from group dip - if you do not then you will get an warning message in the connection log. In most cases this does not matter as the username and password are not actually used or checked by most mobile internet providers - they know who you are from the SIM which is already registered before you can access data. Even so it is best to set these permissions.  use a root file browser which is started in a terminal by:

gksudo nautilus

You then navigate to folder /etc/ppp and right click on pap-secrets -> Properties -> Permissions tab then select dip from the drop down menu for Group and and then select read and write under Access. Repeat for chap-secrets. The annoying warning messages should now disappear.

---

### Post by tlcstat on 2010-01-31
Greetings, 
Thanks alexfish, I followed all of the directions in your post. The chap-secrets file was empty [don't know what that means] but I gave read write permissions on both files for dip. I didn't mention that i was having trouble networking into my phone via bluetooth, but finally got that working after updating to kernel 18. Still in the process of fine tuning that part. But thanks, I'm new to linux and keep forgetting that permissions thing. 
tlcstat

---

### Post by alexfish on 2010-02-01
> **tlcstat said:**
> Greetings, 
Thanks alexfish, I followed all of the directions in your post.  The chap-secrets file was empty [don't know what that means] but I gave read write permissions on both files for dip.  I didn't mention that i was having trouble networking into my phone via bluetooth, but finally got that working after updating to kernel 18.  Still in the process of fine tuning that part.   But thanks, I'm new to linux and keep forgetting that permissions thing. 
tlcstat

hi 

don't know if this will help

[Connecting via Mobile Telephones with inbuilt modems ]("http://www.pcurtis.com/ubuntu-mobile.htm#mobile_telephone")
[LIST]
[*][Bluetooth connection to a Phone Modem]("http://www.pcurtis.com/ubuntu-mobile.htm#bluetooth")
[LIST]
[*][Bluetooth - basics and pairing]("http://www.pcurtis.com/ubuntu-mobile.htm#bluetooth_basic")
[*][Creating a Bluetooth Phone Dial-Up Network Device]("http://www.pcurtis.com/ubuntu-mobile.htm#bt_device")
[/LIST]
[/LIST]

Regards

alexfish

---

### Post by tlcstat on 2010-02-01
Greetings,
Thanks for a great link. I'll go through the list. My phone is working perfectly but there are some things that just aren't right. For instance my rfcomm0 isn't showing up under Gnome-ppp. But it logs in every time from Blueman after I run a script that I use for the usb modem login. The script just puts a link in my NM in the top panel. I will still try to get it right so I will know the process. I have a Moto W845 and just knowing that it will work has made things easier, but right now I think I have a "work around" instead of a correct setup. Typical newbie stuff.
Thanks
tlcstat

---

