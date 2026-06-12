---
title: "No USB devices :("
date: 2011-04-17
forum: General Help
---

### Post by matt-fender on 2011-04-17
Logged in today as usual on my 10.10 machine, and had to download a WLAN driver for a friend, and move it to her laptop. 
     After plugging in a USB flash drive, my card reader AND my mobile phone and not having any luck I realized something was wrong :(

I'm receiving this message from dmesg whenever I insert a USB device


```
[  162.836021] hub 2-0:1.0: unable to enumerate USB device on port 1
[  437.500015] usb 2-1: new full speed USB device using ohci_hcd and address 16
[  437.684016] usb 2-1: device descriptor read/64, error -62
[  437.972015] usb 2-1: device descriptor read/64, error -62
[  438.253014] usb 2-1: new full speed USB device using ohci_hcd and address 17
[  438.436013] usb 2-1: device descriptor read/64, error -62
[  438.725016] usb 2-1: device descriptor read/64, error -62
[  439.004021] usb 2-1: new full speed USB device using ohci_hcd and address 18
[  439.413015] usb 2-1: device not accepting address 18, error -62
[  439.588025] usb 2-1: new full speed USB device using ohci_hcd and address 19
[  439.996022] usb 2-1: device not accepting address 19, error -62
[  439.996032] hub 2-0:1.0: unable to enumerate USB device on port 1
```Kernel V.

```
Linux matthew-desktop 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 19:00:26 UTC 2011 i686 GNU/Linux
```Does anybody have any idea what's going on? Any help greatly appreciated have tried many threads from Google with no luck :(

---

### Post by dragonfly41 on 2011-04-17
is this relevant ...

[http://ubuntuforums.org/showthread.php?t=898939](http://ubuntuforums.org/showthread.php?t=898939)

but it might be "rmmod ohci_hcd" in your case

---

### Post by matt-fender on 2011-04-17
```
ERROR: Module ehci_hcd does not exist in /proc/modules
```ERROR: Module ```
ohci_hcd does not exist in /proc/modules
```


However thanks for your post :)

---

### Post by matt-fender on 2011-04-17
I'm not sure what's going on with this,

I just ran both the commands above ^^ which resulted in errors. Plugged in my Mobile Phone again and now I'm getting this

```
[  439.996032] hub 2-0:1.0: unable to enumerate USB device on port 1
[ 4186.654937] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[ 5065.640022] usb 2-1: new full speed USB device using ohci_hcd and address 20
[ 5065.868718] scsi4 : usb-storage 2-1:1.0
[ 5066.876820] scsi 4:0:0:0: Direct-Access     SonyEric  Mobile Storage  0002 PQ
```

Phone is working again ;)

---

### Post by dragonfly41 on 2011-04-18
command [COLOR=Navy]lsmod[/COLOR] might give some clues as to what is going on ..

[http://www.neowin.net/forum/topic/556286-ubuntu-not-seeing-external-usb-hard-drive/page__st__15](http://www.neowin.net/forum/topic/556286-ubuntu-not-seeing-external-usb-hard-drive/page__st__15)

but at least your mobile is working again.

---

