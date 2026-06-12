---
title: "Net sector on ubuntu"
date: 2011-03-16
forum: General Help
---

### Post by Rakeshvijayan on 2011-03-16
Hello friends 

Is it possible to connect relince netsector to ubuntu os ?if so please help me how to set up

---

### Post by WlaadDyaab on 2011-03-16
> **Rakeshvijayan said:**
> Hello friends 

Is it possible to connect relince netsector to ubuntu os ?if so please help me how to set up

Sorry but has this got something to do with Networking?

It's just that I'm trying to find a tutorial to help you, but the search engines don't understand when I put "netsector in linux" or "net sector linux"

---

### Post by Rakeshvijayan on 2011-03-16
> **WlaadDyaab said:**
> Sorry but has this got something to do with Networking?

It's just that I'm trying to find a tutorial to help you, but the search engines don't understand when I put "netsector in linux" or "net sector linux"


I have netconnector of reliance we always say it is netsector sorry for the word that I used

I got a site "[http://linuxondesktop.blogspot.com/2009/07/configuring-reliance-netconnect-on.html](http://linuxondesktop.blogspot.com/2009/07/configuring-reliance-netconnect-on.html) "It shows the 9.10  I am using 10.10 any one give me the solution

---

### Post by Rakeshvijayan on 2011-03-16
This is the configuration set up  preferred by the site 

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 9600
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0

[Dialer netconnect]
Username =  ( Add your Phone Number here)
Password =  ( Add your phone number here)
Phone = #777
Stupid Mode = 1
Inherits = Modem0


-------------------------------


This image is my file. Is it,  I want change it with site what says

---

### Post by Rakeshvijayan on 2011-03-16
No answer yet what should I do experts

---

### Post by Rakeshvijayan on 2011-03-17
Please any help me how can I see the usb attached devices


this is the result I got when I connect to reliance netconnector

---

### Post by Rakeshvijayan on 2011-03-17
Any body know what is the reason

---

### Post by Rakeshvijayan on 2011-03-17
:) HI FRIENDS FINALY I REACH THE DESTINATION 

HERE IS THE INSTRUCTION WHO USE THE RELIANCE NET CONNECTOR 

1  In order to manually connect with Reliance netconnect broadband we need two packages: **wvdial **(tool to make connections from a modem)and **gnome-ppp **(front end to the wvdial).These two packages have few dependencies too. Means you need to install all of them.

2 download the packages from the following link 

[http://packages.ubuntu.com/uk/lucid/i386/libwvstreams4.6-base/download](http://packages.ubuntu.com/uk/lucid/i386/libwvstreams4.6-base/download)

[http://packages.ubuntu.com/us/lucid/i386/libwvstreams4.6-extras/download](http://packages.ubuntu.com/us/lucid/i386/libwvstreams4.6-extras/download)

[http://packages.ubuntu.com/lucid/i386/libuniconf4.6/download](http://packages.ubuntu.com/lucid/i386/libuniconf4.6/download)

[http://packages.ubuntu.com/lucid/i386/wvdial/download](http://packages.ubuntu.com/lucid/i386/wvdial/download)

[http://packages.ubuntu.com/hardy/i386/gnome-ppp/download](http://packages.ubuntu.com/hardy/i386/gnome-ppp/download)


3   Now bring the above downloaded files to your machine and install them (right click and select *Open with GDebi package installer*) in the **above given order**.

4 Open terminal and then give the command *dmesg *to see which port our model actually using. It would be something like TTYUSB0, TTYUSB1, etc.

5 Now give the command *sudo gnome-ppp * to start the wvdial front end utility.

      GIVE THE USERNAME AND PASSWORD  DEFAULT IT WILL BE PHONE NUMBER
 PHONE NUMBER :#777


6  Now go to setup and in that window select the modem port (/dev/ttyUSB0  for example, which you must have seen in the 4th step using dmesg  command) in the *Device *field and click *detect*. Your modem must be detected now. Then select *Type *as *USB Modem* and select the maximum available speed for the *speed *field.

PRESS DETECT BUTTON RIGHT SIDE OF THE DEVISE :IT WILL AUTOMATICALLY DETECT THE  DEVICE 

7   Click *close *and come back to the *gnome-ppp *front window. Enter the username and password (which is your device number), **#777 **for the number and click connect. Now you should be connected.


                                    *sudo gnome-ppp * to start

ENJOY 

THANKS ALL FRIENDS WHO USE UBUNTU :lolflag:

---

