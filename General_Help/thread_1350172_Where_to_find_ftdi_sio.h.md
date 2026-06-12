---
title: "Where to find ftdi_sio.h"
date: 2009-12-09
forum: General Help
---

### Post by tattee on 2009-12-09
Hi All,

I'm wondering where I could find the ftdi_sio.h file. I have an RFID reader from DLP design and couldn't get the driver to communicate. I have read some instructions on how to make it work and all are telling me to proceed in this directory:

```
~$ cd /usr/src/linux-headers-2.6.27-16-generic/drivers/usb/serial/
```

this is what I could find in the directory:

```
~$ ls
ezusb_convert.pl  Kconfig  Makefile  Makefile-keyspan_pda_fw
```

Please help! I can't proceed with the project until I made those necessary changes on the ftdi_sio.h file. Thanks!

---

### Post by MaindotC on 2009-12-09
****updated****

Any chance you mean this:
```

x@x:~$ sudo locate *.h | grep ftdi
/usr/src/linux-headers-2.6.24-24-generic/include/config/usb/ftdi/elan.h
/usr/src/linux-headers-2.6.24-24-generic/include/config/usb/serial/ftdi/sio.h
/usr/src/linux-headers-2.6.24-25-generic/include/config/usb/ftdi/elan.h
/usr/src/linux-headers-2.6.24-25-generic/include/config/usb/serial/ftdi/sio.h
/usr/src/linux-headers-2.6.24-26-generic/include/config/usb/ftdi/elan.h
/usr/src/linux-headers-2.6.24-26-generic/include/config/usb/serial/ftdi/sio.h
x@x:~$

```



I tried locating it with a Hardy machine no luck:
```

x@x:$ sudo updatedb
x@x:$ find / -iname 'ftdi_sio.h'
find: /home/x/.gvfs: Permission denied
x@x:$

```

You're going to have to find a way to omit that .gvfs directory to conduct the search but that's how you would look at every folder in your filesystem.

---

### Post by tattee on 2009-12-09
Hi strAlan!

I was able to locate the sio.h file but when I tried to open it, it's blank. I'm not really sure if that is the same with ftdi_sio.h. Thanks for your response.:)

Anyone encountered the same problem?

---

### Post by tattee on 2009-12-09
UPDATE!!!

hi strAlan!

I tried to run the second code you posted!

```

root@xxx-laptop:~# updatedb
root@xxx-laptop:~# find / -iname 'ftdi_sio.h'
/usr/src/linux-source-2.6.27/drivers/usb/serial/ftdi_sio.h

```

It showed up and I'm able to edit it! Problem solved! Thanks a lot man! :popcorn:

---

