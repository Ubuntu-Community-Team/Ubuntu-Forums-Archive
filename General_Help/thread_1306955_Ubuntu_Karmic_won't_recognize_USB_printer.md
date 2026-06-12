---
title: "Ubuntu Karmic won't recognize USB printer"
date: 2009-10-30
forum: General Help
---

### Post by arepaking on 2009-10-30
Hello,
I am trying to add a USB printer that worked fine under Jaunty. When I go to system->Administration->Printing and click on Add a new printer.. from the list resulting I cannot see an option for my USB printer.

However, I am able to see an option called "Other" but it asks for an URI which I do not know where to get it for my printer.

Any advice?

Regards,
AK

---

### Post by arepaking on 2009-10-30
I attempted to do the following to try to get the URI on my USB printer but this is what I got:

```
user@user-desktop:~$ sudo /usr/lib/cups/backend/usb
DEBUG: list_devices_libusb
DEBUG: usb_find_busses=8
DEBUG: usb_find_devices=14
Segmentation fault

```

I have no idea what to do folks!

---

### Post by darco on 2009-10-30
I had some issues myself w/Beta....
See if Cups is running

```
ps ax | grep cups
```



if not, try manually starting it

```
service cups start
```

then go back to the menu and see if your printer is recognized


darco

---

### Post by arepaking on 2009-10-30
Hi Darco,
I executed the fist command and this is what I get:

```
 1139 ?        Ss     0:00 /usr/sbin/cupsd -C /etc/cups/cupsd.conf
 9614 pts/0    S+     0:00 grep --color=auto cups
```

I tried to restart CUPS but still won't recognize my USB printer.

---

### Post by darco on 2009-10-30
ok the first command you ran shows the proper response. Did you get any error running the cups restart command?

try this now:

```
http://localhost:631
```

what is the make/model of printer?


darco

---

### Post by arepaking on 2009-10-30
By executing 

```
http://localhost:631
```

I am able to see the CUPS 1.4.1 local site. My printer is a Samsung ML-6060 and I do have a working .PPD file  that I was using on Jaunty.

---

### Post by arepaking on 2009-11-01
Any ideas?

---

### Post by zob on 2009-11-03
We might have the same kind of problem. Does the hardware get recognized at all?
Is there any difference in lsusb before and after you turn on your printer.

---

### Post by zob on 2009-11-05
I have solved my problem. I hope this might solve yours to:

To get a faster boot with a dual-core machine I made a change in /etc/init.d/rc where i changed concurrency=none to concurrency=shell.
Setting it back to concurrency=none solved this problem and another problem I had with Grub.

---

### Post by alanwalterthomas on 2009-11-10
Ok, I used =shell too & I really want that faster boot. I'd like to see =shell enabled by default on multicore systems & also have it work properly, so I really hope this bug is fixed.
Until then, what can I do to have cups start as it should, automatically?
I don't want to have to type /etc/init.d/cups restart every time I print, especially since I share this computer with people who would think that having to type a command to be able to print is absurd.
My only thought right now?
Put this little script in /etc/init.d/
#!/bin/bash
wait 45
/etc/init.d/cups restart
exit

I'm hardly graduated from total noob status so if anyone has a better idea, let me know.

Also, what was the other problem you were having? I'd like to know if I might have it too, & it just hasn't bit me yet.

---

