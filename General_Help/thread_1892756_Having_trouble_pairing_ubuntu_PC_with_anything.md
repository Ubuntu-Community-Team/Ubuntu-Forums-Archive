---
title: "Having trouble pairing ubuntu PC with anything"
date: 2011-12-08
forum: General Help
---

### Post by wagnebr1 on 2011-12-08
I've tried to pair my Ubuntu laptop with both of my phones.  Neither will work.  I've looked at the Ubuntu online help.  It wasn't helpful.

My bluetooth preferences screen looks different than it is shown in the help guides.  I've attahced a screenshot of my bluetooth preferences box.

How do I get my laptop to connect to my phones?

Thanks

---

### Post by lechien73 on 2011-12-08
Sorry, but could I just clarify - is the problem that you can't enable bluetooth in the preferences dialog? Or is it that you can't pair the phones when bluetooth is enabled?

I only ask because of your screenshot showing bluetooth disabled, and I don't want to go off on the wrong track :)

---

### Post by wagnebr1 on 2011-12-08
> **lechien73 said:**
> Sorry, but could I just clarify - is the problem that you can't enable bluetooth in the preferences dialog? Or is it that you can't pair the phones when bluetooth is enabled?

I only ask because of your screenshot showing bluetooth disabled, and I don't want to go off on the wrong track :)

I think both.  I can't enable anything in the bluetooth preferences screen.  However, if click on the bluetooth icon in the top right corner of the desktop, it says bluetooth: on.  I'm assuming that my inability to manipulate anything in the bluetooth preferences menu is preventing me from connecting to anything at this point.

Thanks for the quick reply.

---

### Post by Bucky Ball on 2011-12-08
Visibility also off which would prevent your phone from 'seeing' your computer.

---

### Post by wagnebr1 on 2011-12-08
> **Bucky Ball said:**
> Visibility also off which would prevent your phone from 'seeing' your computer.

I'm not really sure how to fix this either.  Thanks for your interest.

---

### Post by lechien73 on 2011-12-08
I think that Bluetooth may not be working properly. The attached screenshot shows my Bluetooth preferences dialog - the little Bluetooth icon in the top right corner of the desktop also says that Bluetooth is on.

Is there a hardware switch for Bluetooth on your machine? For example either a switch on the side, or pressing Fn and a function key?

If you can't set Bluetooth to enabled in the preferences dialog, then that indicates it isn't working.

Could you run:

```
dmesg | grep Bluetooth
```

And post the output here between CODE tags (the **#** button on the toolbar), please?

---

### Post by wagnebr1 on 2011-12-08
> **lechien73 said:**
> I think that Bluetooth may not be working properly. The attached screenshot shows my Bluetooth preferences dialog - the little Bluetooth icon in the top right corner of the desktop also says that Bluetooth is on.

Is there a hardware switch for Bluetooth on your machine? For example either a switch on the side, or pressing Fn and a function key?

If you can't set Bluetooth to enabled in the preferences dialog, then that indicates it isn't working.

Could you run:

```
dmesg | grep Bluetooth
```And post the output here between CODE tags (the **#** button on the toolbar), please?


```
brian@brian-Inspiron-N5010:~$ dmesg | grep Bluetooth
[   19.920520] Bluetooth: Core ver 2.16
[   19.920550] Bluetooth: HCI device and connection manager initialized
[   19.920552] Bluetooth: HCI socket layer initialized
[   19.920554] Bluetooth: L2CAP socket layer initialized
[   19.920613] Bluetooth: SCO socket layer initialized
[   19.922609] Bluetooth: RFCOMM TTY layer initialized
[   19.922615] Bluetooth: RFCOMM socket layer initialized
[   19.922617] Bluetooth: RFCOMM ver 1.11
[   19.944565] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.944569] Bluetooth: BNEP filters: protocol multicast
brian@brian-Inspiron-N5010:~$ 


```

---

### Post by wagnebr1 on 2011-12-09
Anyone got ideas?

---

### Post by lechien73 on 2011-12-09
Sorry, I was in meetings most of yesterday and today.

When you click on the button to enable Bluetooth, does it change to "On" or remain at "Off"?

Have you tried some of the troubleshooting steps in these docs:

[https://help.ubuntu.com/11.04/ubuntu-help/hardware.html#bluetooth](https://help.ubuntu.com/11.04/ubuntu-help/hardware.html#bluetooth)
[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

---

### Post by wagnebr1 on 2011-12-11
> **lechien73 said:**
> Sorry, I was in meetings most of yesterday and today.

When you click on the button to enable Bluetooth, does it change to "On" or remain at "Off"?

Have you tried some of the troubleshooting steps in these docs:

[https://help.ubuntu.com/11.04/ubuntu-help/hardware.html#bluetooth](https://help.ubuntu.com/11.04/ubuntu-help/hardware.html#bluetooth)
[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

Thanks for your help.  I went back and installed the drivers in Windows7 (I have a dual boot Dell), and now the Bluetooth in Ubuntu "works".  

I put works in quotes because I successfully paired my phone (DROID RAZR) to my Laptop (Dell Inspiron 15 R N5010).  However, I can't get them to connect.  

Is this an Ubuntu driver problem?

---

