---
title: "Error: failed to set system time"
date: 2009-07-20
forum: General Help
---

### Post by oxf on 2009-07-20
I've noticed recently that my system clock was exactly one hour ahead of the correct time.
So I right clicked on the time in upper right of the desktop and selected "adjust date and time" and changed it. When I click " set system time" and enter password I get the following error message:

"Failed to set system time 
/bin/hwclock    returned 256"

Now the time actually does change but only until I reboot, then its off again. Anyone know what going on here?

For now I have reset it by going into the bios setup and dong it that way but I should really be able to change it from inside the OS.

---

### Post by michy99 on 2009-07-20
What output do you get from```
ls /dev/rtc*
```Also, can you set the correct time using System > Administration > Time and Date?

---

### Post by oxf on 2009-07-21
> **michy99 said:**
> What output do you get from```
ls /dev/rtc*
```Also, can you set the correct time using System > Administration > Time and Date?

I can change the time via System/Admin and I dont get the error message but as before it loses the change upon reboot 

and???:

~$ ls /dev/rtc*
ls: cannot access /dev/rtc*: No such file or directory


Thanks

---

### Post by credobyte on 2009-07-21
Try to change your time again ( to generate the error again ) and execute this command ( post the output ) :
```
cat /var/log/syslog | grep ntpd
```

---

### Post by oxf on 2009-07-21
> **credobyte said:**
> Try to change your time again ( to generate the error again ) and execute this command ( post the output ) :
```
cat /var/log/syslog | grep ntpd
```

I only get the error msg if i do it by right clicking on the clock. Result is the same though.

mbdb@L100:~$ cat /var/log/syslog | grep ntpd
Jul 21 13:45:08 L100 ntpdate[6979]: adjust time server 91.189.94.4 offset -0.377581 sec
Jul 21 14:30:50 L100 ntpdate[8344]: adjust time server 91.189.94.4 offset -0.232835 sec
Jul 21 14:35:18 L100 ntpdate[3317]: step time server 91.189.94.4 offset 2.403941 sec
mbdb@L100:~$

---

### Post by oxf on 2009-07-22
bump

---

### Post by QIII on 2009-07-22
Try this:

```
sudo gedit /etc/default/rcS
```or 

```
gksu gedit /etc/default/rcS
```Look for 

```
UTC=yes
```and change it to

```
UTC=no
```But I find it odd that your clock is showing 1 hour ahead, since I think you are at GMT + 1 during BST...

Hmmm.

---

### Post by michy99 on 2009-07-22
> **oxf said:**
> I can change the time via System/Admin and I dont get the error message but as before it loses the change upon reboot 

and???:

~$ ls /dev/rtc*
ls: cannot access /dev/rtc*: No such file or directory


Thanks

This may be part of the problem. hwclock uses /dev/rtc to access the system real time clock. What do you get for:```
cat /proc/devices
```

---

### Post by oxf on 2009-07-23
> **QIII said:**
> Try this:

```
sudo gedit /etc/default/rcS
```or 

```
gksu gedit /etc/default/rcS
```Look for 

```
UTC=yes
```and change it to

```
UTC=no
```But I find it odd that your clock is showing 1 hour ahead, since I think you are at GMT + 1 during BST...

Hmmm.

Right I dont think its a UTC issue. Yes we are  GMT + 1 right now and this is GMT + 2 But the real issue is not what it is because I can set it by going into Bios Setup. Its the fact I cant set it from the desk top

---

### Post by oxf on 2009-07-23
> **michy99 said:**
> This may be part of the problem. hwclock uses /dev/rtc to access the system real time clock. What do you get for:```
cat /proc/devices
```

This is what I got:

mbdb@L100:~$ cat /proc/devices
Character devices:
  1 mem
  4 /dev/vc/0
  4 tty
  4 ttyS
  5 /dev/tty
  5 /dev/console
  5 /dev/ptmx
  6 lp
  7 vcs
 10 misc
 13 input
 14 sound
 21 sg
 29 fb
 99 ppdev
108 ppp
116 alsa
128 ptm
136 pts
171 ieee1394
180 usb
188 ttyUSB
189 usb_device

---

### Post by michy99 on 2009-07-23
> **oxf said:**
> This is what I got:

mbdb@L100:~$ cat /proc/devices
Character devices:
  1 mem
  4 /dev/vc/0
  4 tty
  4 ttyS
  5 /dev/tty
  5 /dev/console
  5 /dev/ptmx
  6 lp
  7 vcs
 10 misc
 13 input
 14 sound
 21 sg
 29 fb
 99 ppdev
108 ppp
116 alsa
128 ptm
136 pts
171 ieee1394
180 usb
188 ttyUSB
189 usb_device

Very odd that your not showing a rtc. This is what I get:```
mike@ubuntumike:~$ cat /proc/devices
Character devices:
  1 mem
  4 /dev/vc/0
  4 tty
  4 ttyS
  5 /dev/tty
  5 /dev/console
  5 /dev/ptmx
  6 lp
  7 vcs
 10 misc
 13 input
 14 sound
 21 sg
 29 fb
 99 ppdev
108 ppp
116 alsa
128 ptm
136 pts
180 usb
189 usb_device
216 rfcomm
226 drm
251 hidraw
252 usb_endpoint
253 usbmon
254 rtc


```I notice your list ends at 189. Is it possible you truncated it when copying?

Try this and see if it creates a /dev/rtc.```
mknod c /dev/rtc 254 0
ls /dev/rtc*
```

---

### Post by oxf on 2009-07-24
> **michy99 said:**
> Very odd that your not showing a rtc. 

[/code]I notice your list ends at 189. Is it possible you truncated it when copying?

Try this and see if it creates a /dev/rtc.```
mknod c /dev/rtc 254 0
ls /dev/rtc*
```

Well I could have sworn I didn't but I must have! And yes rtc is there tis time.

mbdb@L100:~$ cat /proc/devices
Character devices:
  1 mem
  4 /dev/vc/0
  4 tty
  4 ttyS
  5 /dev/tty
  5 /dev/console
  5 /dev/ptmx
  6 lp
  7 vcs
 10 misc
 13 input
 14 sound
 21 sg
 29 fb
 99 ppdev
108 ppp
116 alsa
128 ptm
136 pts
171 ieee1394
180 usb
188 ttyUSB
189 usb_device
216 rfcomm
251 hidraw
252 usb_endpoint
253 usbmon
254 rtc

Block devices:
  1 ramdisk
259 blkext
  7 loop
  8 sd
  9 md
 11 sr
 65 sd
 66 sd
 67 sd
 68 sd
 69 sd
 70 sd
 71 sd

---

### Post by michy99 on 2009-07-24
Did you try the mknod command from my earlier post?

---

### Post by oxf on 2009-07-24
> **michy99 said:**
> Did you try the mknod command from my earlier post?

mbdb@L100:~$ mknod c /dev/rtc 254 0
mknod: invalid device type `/dev/rtc'
Try `mknod --help' for more information.
mbdb@L100:~$ 

What am I trying to do with this code?
Thanks so far!

---

### Post by oxf on 2009-07-28
any more ideas?

---

### Post by oxf on 2009-07-29
bump

---

### Post by mister_p_1998 on 2009-07-29
I had trouble with this when I was dual-booting with XP, XP will try to reset the bIOS time when it runs. Linux leaves the BIOS time on GMT all the time and adds or subtracts an hour according to whether its BST or GMT. Windows confuses Linux on a dual-bot system cause it changes it to whatever the time is at the moment. Leave your BIOS time on GMT (if youre in the UK) and let the OS adjust for Summer/Winter.
Steve

---

### Post by oxf on 2009-07-29
> **mister_p_1998 said:**
> I had trouble with this when I was dual-booting with XP, XP will try to reset the bIOS time when it runs. Linux leaves the BIOS time on GMT all the time and adds or subtracts an hour according to whether its BST or GMT. Windows confuses Linux on a dual-bot system cause it changes it to whatever the time is at the moment. Leave your BIOS time on GMT (if youre in the UK) and let the OS adjust for Summer/Winter.
Steve

Thanks. Yes I am dual booting. I can see that might be the case explaining why the clock gets off in the first place and your sugestion would take care of it. However, that doesnt explain (i dont think?) why I cant change it and I get the erro message. eg if my clock is say 5 minutes off and I try to correct it I get the error message. In reality though it does change it for that session only and then when I reboot its off again. For now I'm just changing it in the bios setup until I find  a solution

---

### Post by mister_p_1998 on 2009-07-30
> **oxf said:**
> Thanks. Yes I am dual booting. I can see that might be the case explaining why the clock gets off in the first place and your sugestion would take care of it. However, that doesnt explain (i dont think?) why I cant change it and I get the erro message. eg if my clock is say 5 minutes off and I try to correct it I get the error message. In reality though it does change it for that session only and then when I reboot its off again. For now I'm just changing it in the bios setup until I find  a solution

do have have to sudo a time change?
Why not just set up NTP to set the clock off the internet?
Steve

---

### Post by oxf on 2009-08-04
> **mister_p_1998 said:**
> I had trouble with this when I was dual-booting with XP, XP will try to reset the bIOS time when it runs. Linux leaves the BIOS time on GMT all the time and adds or subtracts an hour according to whether its BST or GMT. Windows confuses Linux on a dual-bot system cause it changes it to whatever the time is at the moment. Leave your BIOS time on GMT (if youre in the UK) and let the OS adjust for Summer/Winter.
Steve

Where exactly in Ubuntu is the option to have the system automatically adjust the time from GMT to BST set?

Thanks

---

### Post by mister_p_1998 on 2009-08-25
> **oxf said:**
> Where exactly in Ubuntu is the option to have the system automatically adjust the time from GMT to BST set?

Thanks

Right button over your date/time on the taskbar, select 'Adjust date and time' and choose 'Syncronise with Internet Time Servers'

Steve

---

