---
title: "Canon LBP2900 make it work, work - make it work"
date: 2012-09-12
forum: General Help
---

### Post by deff182 on 2012-09-12
I've got xubuntu 12.04 x64 release. I want to add canon lbp2900 support. I've followed [this tutorial]("https://help.ubuntu.com/community/CanonCaptDrv190") and spent a ridiculous amount of time - crazy :lolflag:

I've installed the printer.


```
midnight@midnight:~$ sudo ccpdadmin


 CUPS_ConfigPath = /etc/cups/
 LOG Path        = None
 UI Port         = 59787

 Entry Num  : Spooler	: Backend	: FIFO path		: Device Path 	: Status 
 ----------------------------------------------------------------------------
     [0]    : LBP2900 	: ccp 		: //localhost:59787 	: /dev/usb/lp0 	: 
```

I've made sure usblp is present:

```
midnight@midnight:~$ lsmod | grep usblp
usblp                  18307  0 
```

This is the /etc/ccpd.conf file:

```
<Path>
CUPS_ConfigPath   /etc/cups/
</Path>


<Printer LBP2900>
DevicePath /dev/usb/lp0
</Printer>

<Ports>
# Status monitoring socket port.
#  Default 59787
UI_Port  59787
PDATA_Port  59687
</Ports>
```

When I try to print a test-page dialogs look like this:
[IMG]http://i.imgur.com/i4n2y.png[/IMG]
[IMG]http://i.imgur.com/wArDW.png[/IMG]

Any help ?

---

