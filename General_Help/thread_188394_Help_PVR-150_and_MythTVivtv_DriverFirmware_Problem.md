---
title: "Help: PVR-150 and MythTV/ivtv Driver/Firmware Problem"
date: 2006-06-04
forum: General Help
---

### Post by ferretshock on 2006-06-04
Hey all-

I've been trying for the past few days to get MythTV up and running (specifically the ivtv driver, at this point) on dapper.  I'm new to ubuntu and its been a while since I last really used linux, so there might be a few things that are unclear to me.

Anyway, I've been folowing how to guides for getting mythtv set up on ubuntu, namely these:

[http://hyams.webhop.net/mythtv/myth_ubuntu.html]("http://hyams.webhop.net/mythtv/myth_ubuntu.html")
[http://www.abarbaccia.com/content/view/15/29/]("http://www.abarbaccia.com/content/view/15/29/")

And then specifically for the ivtv driver/firmware:
[http://www.ivtvdriver.org/index.php/Howto]("http://www.ivtvdriver.org/index.php/Howto")

And I also came across [this thread]("http://www.ubuntuforums.org/showthread.php?t=186747&highlight=%2Fdev%2Fvideo0") which described a few differences in dapper, since the above guides were written for breezy.  I'm not sure how much difference there actually is, since I'm new to ubuntu and whatnot.

So, I've tried to go through these guides twice, both times making it to the ivtv driver installation and verification.  Everything is going just fine until I go to create the test.mpg file, when it gives me this message:

```
root@fantasia:/lib/firmware# cat /dev/video0 > /tmp/test.mpg
cat: /dev/video0: No such file or directory
```

Anyway, the problem (or what I believe the problem to be) is that I think my firmware isn't installed in the right place.  I've tried copying it to any sort of hotplug/firmware directory I saw mentioned on different guides, but have yet to have any luck.  This is the relevant section of the dmesg output:

```
[4294690.628000] ivtv: no version for "struct_module" found: kernel tainted.
[4294690.631000] ivtv:  ==================== START INIT IVTV ====================
[4294690.631000] ivtv:  version 0.4.5 (tagged release) loading
[4294690.631000] ivtv:  Linux version: 2.6.15.7-ubuntu1 preempt 486 gcc-4.0
[4294690.631000] ivtv:  In case of problems please include the debug info between
[4294690.631000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[4294690.631000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[4294690.631000] ivtv0: Autodetected WinTV PVR 150 card (cx23416 based)
[4294690.632000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[4294691.120000] tveeprom: ivtv version
[4294691.120000] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[4294691.154000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #0
[4294691.154000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[4294691.415000] cx25840 2-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[4294691.588000] ivtv0: i2c attach to card #0 ok [client=cx25840, addr=44]
[4294691.634000] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #0)
[4294691.645000] ivtv0: i2c attach to card #0 ok [client=wm8775, addr=1b]
[4294692.330000] ivtv0: unable to open firmware v4l-cx2341x-enc.fw
[4294692.330000] ivtv0: did you put the firmware in the hotplug firmware directory?
[4294692.330000] ivtv0 warning: failed loading encoder firmware
[4294692.330000] ivtv0 warning: Error loading firmware -3!
[4294692.330000] ivtv0: Error -3 initializing firmware.
[4294692.332000] ivtv0: Error -12 on initialization
[4294692.332000] ivtv: probe of 0000:01:06.0 failed with error -12
[4294692.332000] ivtv:  ====================  END INIT IVTV  ====================
```

And the output from an ls -ltra /lib/firmware/ :

```
total 1080
drwxr-xr-x  3 root root   4096 May 30 20:53 2.6.15-23-386
-rw-r--r--  1 root root 262144 Jun  3 21:11 ivtv-fw-enc.bin
-rw-r--r--  1 root root 262144 Jun  3 21:11 ivtv-fw-dec.bin
-r--r--r--  1 root root  14264 Jun  3 21:11 v4l-cx25840.fw
-r--r--r--  1 root root 376836 Jun  3 21:12 v4l-cx2341x-enc.fw
-rw-r--r--  1 root root 155648 Jun  3 21:13 v4l-cx2341x-init.mpg
lrwxrwxrwx  1 root root     28 Jun  3 21:13 v4l-cx2341x-dec.fw -> lib/firmware/ivtv-fw-dec.bin
drwxr-xr-x  3 root root   4096 Jun  3 21:13 .
drwxr-xr-x 20 root root   4096 Jun  3 23:53 ..
```

Again, I'm not sure that I put things in exactly the right place, so that could be it, or it could even be something really stupid.  But if anyone's ever seen this before, or knows what to do about it, any pointers would be really appreciated, since this is me right now: ](*,)

---

### Post by Titus A Duxass on 2006-06-04
This comes up quite often with myth.
First - my recommendation is to ignore the problem with the test.mpg, I never got it to work but my system is fine.

Second - If you read the ivtv webpages it does give you a guide.  Shutdown the Pooter, unplug it, wait 30 seconds and then reboot.

If you have all the firmware files in the right place it will work.

---

### Post by ferretshock on 2006-06-04
Hm, it seems like it really was just that the computer needed to be really off.  I came back to it after my computer being off for a few hours and now it recognizes the driver and everything.  I guess they were really serious about it taking a while for the registers to clear...

Thanks:-D 

> This comes up quite often with myth.
First - my recommendation is to ignore the problem with the test.mpg, I never got it to work but my system is fine.

Second - If you read the ivtv webpages it does give you a guide. Shutdown the Pooter, unplug it, wait 30 seconds and then reboot.

If you have all the firmware files in the right place it will work.

---

### Post by scifan on 2006-06-13
That sounds like you've got an IRQ conflict... 

Try checking your system to see if you might have something else that's interfering with your IRQ...

Also, downgrade from IVTV 0.4.5 to 0.4.4... there are issue's with 0.4.5 (spent most of the last two day's trying to figure out why my system would freeze when changing channel's...)

best of luck.

---

