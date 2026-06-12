---
title: "usb phone adapter - HID permissions"
date: 2006-04-11
forum: General Help
---

### Post by tiepolo on 2006-04-11
Hallo to everybody!

I'm trying to configure a usb phone adapter from cuphone, which i installed via alien from a .rpm  file.

Sound card is recognized, but the program asks me to grant permission to HID devices in order to dial and receive calls.

Does anybody know how to do that?

I also tried to compile the program from the source, but the ./Configure instruction is not executed.

thanks in advance, 

Paolo:rolleyes:

---

### Post by jasona228 on 2007-08-18
I'm having a slightly different bit of trouble.  I set the permissions as follows to get to where I am now.  

I took the information found at the following web link and searched around for something close to what they were suggesting:

[http://www.cuphone.com/help/linux.htm#skype](http://www.cuphone.com/help/linux.htm#skype)

Here are the commands I used to set permissions on my Feisty box.  I tried to find the closest matches to what they were suggesting:

I opened up a terminal session and ran the following:

cd /dev/.udev/names/hiddev0
sudo chmod 666 *

cd /etc/udev/rules.d
sudo chmod 666 99-udevmonitor.rules

However...  Now when I start the tjinit_skype, I get the following error:

TigerJet USB Phone Device[B] is ready
Hardware initiated successfully
6175: arguments to dbus_connection_send_with_reply_and_block() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 1996.
This is normally a bug in some application using the D-BUS library.
Program aborts :: Please logon your skype at first !!!

I do have skype running, so I'm not sure what it's complaining about at this point.  Any ideas would be welcome!  

J

---

### Post by pcreed on 2007-12-03
One of my problems is that /dev/.udev/names/hiddev0 doesn't even exist. Did you have to set something up in order to get this directory created?

---

