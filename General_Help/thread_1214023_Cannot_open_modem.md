---
title: "Cannot open modem"
date: 2009-07-15
forum: General Help
---

### Post by sundar261 on 2009-07-15
Hi,

I am having issues with my internet connectivity through datacard.  I have USB modem (Huawei Technologies Co., Ltd. E620 USB Modem). I connect to internet through Gnome PPP utility.  The connection works fine when I connect it for the first time.  But have a problem when it disconnects due to poor signal.  When I reconnect I get a message "Cannot open modem".  Even removing the modem and putting it back after some time does not help.  The problem is solved only when I restart the laptop.  

Any pointer in resolving the issue will be of great help to me.  

To me it looks like a Linux problem with the usb modem.  Not sure the resources are held when the first failure happens and is not cleared properly.  I would get the same error message if I have a PPP connection and try to connect again.   

I am running it on a Lenovo N100 laptop with Ubuntu 8.04.

-Sundar

---

### Post by kilowattradio on 2009-07-15
> **sundar261 said:**
> Hi,

I am having issues with my internet connectivity through datacard.  I have USB modem (Huawei Technologies Co., Ltd. E620 USB Modem). I connect to internet through Gnome PPP utility.  The connection works fine when I connect it for the first time.  But have a problem when it disconnects due to poor signal.  When I reconnect I get a message "Cannot open modem".  Even removing the modem and putting it back after some time does not help.  The problem is solved only when I restart the laptop.  

Any pointer in resolving the issue will be of great help to me.  

To me it looks like a Linux problem with the usb modem.  Not sure the resources are held when the first failure happens and is not cleared properly.  I would get the same error message if I have a PPP connection and try to connect again.   

I am running it on a Lenovo N100 laptop with Ubuntu 8.04.

-Sundar

You need to check your permissions and what group the modem is in for users. 

```

ls -l /dev/tty*  (or whatever it is)
crw-rw-r--  1 root  wheel   17,   3 Jul 15 08:34 /dev/tty.Bluetooth-Modem
crw-rw-r--  1 root  wheel   17,   1 Jul 15 08:34 /dev/tty.Bluetooth-PDA-Sync

```
This device belongs to the wheel group so go into Groups and Users and add your user ID/Name to the wheel group or whatever it is.

---

### Post by ramnarayan on 2009-07-15
Sundar it would be helpful if you posted your question just once
 repeated posting is a waste of time and resources

you posted the same thing at
[http://ubuntuforums.org/showthread.php?t=1214044](http://ubuntuforums.org/showthread.php?t=1214044)

---

