---
title: "Ubuntu 10.04 Lucid Lynx Session Freezes"
date: 2011-07-15
forum: General Help
---

### Post by george5729 on 2011-07-15
I was wondering if anybody else was experiencing this problem.

My ubuntu session will freeze and stop working. For example, the mouse and the keyboard will stop responding and the screen sometimes get divided into 4 smaller quadrants of the  current screen.

The only thing I can do after it freezes is reboot the machine.

Would anyone know what is causing this?

Also, I keep having to move my optical mouse from the usb slot into a ps/2 slot.
And the same thing with my keyboard. I have 2 keyboards, so I can plug in the old ps/2 keyboard instead of the new usb keyboard. (the devices keep flipping)

My machine is an AMD 3400 with an Epox mobo. Nothing like this has ever happened before, and I have been using ubuntu for more than 4 years without any problems.

Thanks,
George

---

### Post by wildmanne39 on 2011-07-16
Hi, after it freezes and you reboot go right into dmesg log and see what errors you get. You can use log file viewer to see the logs.

---

### Post by DawieS on 2011-07-16
> **george5729 said:**
> I was wondering if anybody else was experiencing this problem.

My ubuntu session will freeze and stop working. For example, the mouse and the keyboard will stop responding and the screen sometimes get divided into 4 smaller quadrants of the  current screen.

The only thing I can do after it freezes is reboot the machine.

Would anyone know what is causing this?

Also, I keep having to move my optical mouse from the usb slot into a ps/2 slot.
And the same thing with my keyboard. I have 2 keyboards, so I can plug in the old ps/2 keyboard instead of the new usb keyboard. (the devices keep flipping)

My machine is an AMD 3400 with an Epox mobo. Nothing like this has ever happened before, and I have been using ubuntu for more than 4 years without any problems.

Thanks,
George
Hi, and welcome to the forums!:smile::smile:

When you have a problem, it is best practice to do a good search on the forum, and maybe add your problem as a post to an existing thread, instead of creating a new thread. In this way you may:
- see if the problem manifests in a specific hardware group of users, or a specific configuration of the software.
- may contribute towards the compilation of a bug report, which will have a higher priority affecting a large number of users.
- subscribe to the thread, and try possible workarounds that other users (with the same problem) may have found.

You may want to ask a moderator to merge your thread into [_**this thread**_]("http://ubuntuforums.org/showthread.php?t=1478787").

---

### Post by george5729 on 2011-07-18
Thank you for the reply Widlman.

Here is what I see when I do a dmesg:

[   18.501669] fbcon: radeondrmfb (fb0) is primary device
[   18.502841] Console: switching to colour frame buffer device 210x65
[   18.502908] fb0: radeondrmfb frame buffer device
[   18.502910] drm: registered panic notifier
[   18.502987] [drm] Initialized radeon 2.8.0 20080528 for 0000:01:00.0 on minor 0
[   18.504468] intel8x0_measure_ac97_clock: measured 55841 usecs (2744 samples)
[   18.504471] intel8x0: clocking to 46887
[   18.704482] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   18.968867] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   19.184125] ivtv0: Encoder revision: 0x02060039
[   23.565326] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   25.130625] cx25840 2-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   25.470685] audit_printk_skb: 18 callbacks suppressed
[   25.470689] type=1400 audit(1311044242.167:18): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1278 comm="apparmor_parser"
[   25.471179] type=1400 audit(1311044242.167:19): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1278 comm="apparmor_parser"


Can you please explain what I am looking for?


Please note, I have upgraded from Lucid Lynx to Natty in the hopes this problem would go away, but it hasn't.

Today my optical USB Logitech mouse stopped responding and again I had to do reboot my system.

I will continue to read the forums for more information. If anybody has a link with related info, please point me in that direction.

Thanks for the help,
george5729

---

### Post by wildmanne39 on 2011-07-18
Hi, we are looking for any errors but I saw none in what you posted. You can also run system log and see what it says. 

Here is a link on freezing it might help.
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

---

### Post by george5729 on 2011-07-19
Thanks for the link. I will read the information.

Also, I have replaced my usb mouse and keyboard with my old ps/2 mouse and keyboard.

It seems to be working as of right now. I am keeping my fingers crossed.

---

### Post by wildmanne39 on 2011-07-19
> **george5729 said:**
> Thanks for the link. I will read the information.

Also, I have replaced my usb mouse and keyboard with my old ps/2 mouse and keyboard.

It seems to be working as of right now. I am keeping my fingers crossed.Hi, keep us informed and if the link fixes your problem  would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

### Post by george5729 on 2011-07-20
The link was helpful, but it did not resolve my problem.

At boot up I hold the delete key and went into the machine BIOS.

I noticed my BIOS was changed all by itself. (How's this happening?)
I had to reset the clock in the BIOS to today's date 2011.
And again I had to disable the USB from V1.1 + v2.1 to DISABLED.

I started my machine with USB disabled. Whenever it gets enabled, the machine freezes.
I'm guessing because it wants to use a usb keyboard and mouse.

I will check with epox mobo to see if there is a firmware upgrade to fix this problem.

---

### Post by wildmanne39 on 2011-07-20
Hi, the issue with the bios changing sounds like the round battery in your computer may need to be replaced, and be careful if you are thinking about upgrading the bios sometimes it works sometimes it makes things worse.

---

### Post by george5729 on 2011-07-24
I have not had any problems for a while. I'm guessing things are ok now that I'm not using my USB wireless mouse or USB keyboard and booting up with my old ps/2 mouse and kb.

I have changed the the nickel sized battery before (last February), it's fairly new, so I don't think that is the problem with the BIOS. Also, EPOX I think is out of business. I can't find a new BIOS for my old mobo.

Question:
What will happen to the old hardware when USB 3.0 is released? Will it be compatible? Could this be causing freaky behavior with USB components?

I'm thinking it might be time to upgrade my entire system to something new... a new cpu and motherboard.

Cheers!

---

### Post by wildmanne39 on 2011-07-24
Hi, usb 3.0 should be compatible with your system but it will run at the slower speed if your system does not support 3.0. Depending on how old your system is it might be worth upgrading but if it is real old then I would save my money and replace the computer.

---

### Post by george5729 on 2011-09-09
I have arrived at the point where I can make my machine crash on demand.

All I have to do is open a session of Google Maps and go down to the street level map where you can see pictures of the street with detail.

And my machine will always freeze on that level of detail with either Firefox or the Chrome Web Browser.

I'm thinking this happens because there is something my with Graphics Card (ATI Radeon) which it can't handle. And this did not happen before with earlier version of Ubuntu.

If anybody has any suggestions (other than buying new HW), please let me know.

:~$ lsb_release -d -s -c
Ubuntu 11.04
natty

Thank you and kind regards.

---

### Post by george5729 on 2011-09-09
I came across this article:
[COLOR=Blue]
[http://ubuntuguide.net/ubuntu-11-04-upgrade-linux-kernel-to-2-6-39-0](http://ubuntuguide.net/ubuntu-11-04-upgrade-linux-kernel-to-2-6-39-0)[/COLOR]

And I have tried upgrading the kernel from 2.6.38 to 2.6.39, but I have not been able to make it work.

According to the instructions, kernel 2.6.39.0 should be in list below, but I don't see it.

sudo add-apt-repository ppa:kernel-ppa/ppa  sudo apt-get updateapt-cache showpkg linux-headers
:~$ apt-cache showpkg linux-headers
Package: linux-headers
Versions: 

Reverse Depends: 
  virtualbox-4.1,linux-headers
  oss4-dkms,linux-headers
  lirc-modules-source,linux-headers
  sl-modem-source,linux-headers
  xtables-addons-dkms,linux-headers
  oss4-dkms,linux-headers
  openswan-modules-source,linux-headers
  lirc-modules-source,linux-headers
  blcr-dkms,linux-headers
  alsa-source,linux-headers
  nvidia-current,linux-headers
  nvidia-96,linux-headers
  nvidia-173,linux-headers
  fglrx,linux-headers
  bcmwl-kernel-source,linux-headers
  dkms,linux-headers
Dependencies: 
Provides: 
Reverse Provides: 
linux-headers-2.6.38-11-virtual 2.6.38-11.48
linux-headers-2.6.38-11-generic-pae 2.6.38-11.48
linux-headers-2.6.38-11-generic 2.6.38-11.48
linux-headers-2.6.38-11 2.6.38-11.48
linux-headers-2.6.38-10-virtual 2.6.38-10.46
linux-headers-2.6.38-10-generic-pae 2.6.38-10.46
linux-headers-2.6.38-10-generic 2.6.38-10.46
linux-headers-2.6.38-10 2.6.38-10.46
linux-headers-2.6.38-8-virtual 2.6.38-8.42
linux-headers-2.6.38-8-generic-pae 2.6.38-8.42
linux-headers-2.6.38-8-generic 2.6.38-8.42
linux-headers-2.6.38-8 2.6.38-8.42



Any suggestions are greatly appreciated.
Thanks and kind regards

---

### Post by wildmanne39 on 2011-09-09
Hi, post the results of this command here please:
```
lsmod
```
Thank you

---

### Post by george5729 on 2011-09-09
$ lsmod 

Module                  Size  Used by
binfmt_misc            13213  1 
tuner_simple           18134  1 
tuner_types            18907  1 tuner_simple
wm8775                 12902  1 
snd_wavefront          34696  0 
tuner                  26802  1 
snd_cs4236             29291  0 
cx25840                48549  1 
snd_wss_lib            30006  2 snd_wavefront,snd_cs4236
pci_stub               12550  1 
snd_opl3_lib           18760  2 snd_wavefront,snd_cs4236
snd_intel8x0           33213  2 
vboxpci                22892  0 
snd_hwdep              13274  2 snd_wavefront,snd_opl3_lib
snd_mpu401             13800  0 
vboxnetadp             13348  0 
vboxnetflt             27225  0 
snd_mpu401_uart        13865  3 snd_wavefront,snd_cs4236,snd_mpu401
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
radeon                900494  3 
snd_pcm                80042  4 snd_cs4236,snd_wss_lib,snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  3 snd_wavefront,snd_mpu401_uart,snd_seq_midi
vboxdrv               251892  3 vboxpci,vboxnetadp,vboxnetflt
snd_seq_midi_event     14475  1 snd_seq_midi
ivtv                  143431  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ttm                    65184  1 radeon
snd_timer              28659  4 snd_wss_lib,snd_opl3_lib,snd_pcm,snd_seq
cx2341x                27688  1 ivtv
drm_kms_helper         40745  1 radeon
snd_seq_device         14110  4 snd_opl3_lib,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                  12849  0 
drm                   184164  5 radeon,ttm,drm_kms_helper
v4l2_common            16757  5 wm8775,tuner,cx25840,ivtv,cx2341x
ns558                  12618  0 
gameport               15027  2 ns558
videodev               75143  6 wm8775,tuner,cx25840,ivtv,cx2341x,v4l2_common
serio_raw              12990  0 
snd                    55295  18 snd_wavefront,snd_cs4236,snd_wss_lib,snd_opl3_lib,snd_hwdep,snd_mpu401,snd_mpu401_uart,snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13184  2 radeon,ivtv
tveeprom               17009  1 ivtv
parport_pc             32111  1 
soundcore              12600  1 snd
k8temp                 12872  0 
snd_page_alloc         14073  3 snd_wss_lib,snd_intel8x0,snd_pcm
shpchp                 32345  0 
i2c_nforce2            12906  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
floppy                 60032  0 
pata_amd               13762  2 
sata_nv                23176  0 
forcedeth              58190  0

---

### Post by wildmanne39 on 2011-09-09
Hi, please post the results of these commands right after you get back into your computer after it has frozen.
```
dmesg |tail -n300
```
```
tail -n200 /var/log/syslog
```
```
tail -n200 /var/log/kern.log
```
Thank you

---

### Post by george5729 on 2011-09-10
Wildmanne,

Can I email those results to you?
My email is [EMAIL="george5729@ymail.com"]george5729@ymail.com[/EMAIL]

I get this message when I try to cut an paste...
{
The text that you have entered is too long (20821 characters). Please shorten it to 5000 characters long.
}

I made my machine crash by running Google Maps, as I have mentioned in my previous posts.

I ran your commands before and after crashing.
And I can also send the before files, if you need them.

Thank you and kind regards,
George

---

### Post by wildmanne39 on 2011-09-10
Hi, I replied to your message but my email encrypted it so I do not know if you were able to read it and yes I will look over your logs in my email.

I will being checking my email often for them.
Thank you

---

### Post by george5729 on 2011-09-10
I installed all the ATI software in the "Ubuntu Software Center" by doing a search for "ATI", and re-booting my machine.

I got the following message:

"It seems that you do not have the hardware required to run Unity. Please choose Ubuntu Classic at the login screen and you will be using the traditional environment."

I have the following Installed Software on my machine:
ATI binary X.Org driver
xatitv
gatos-conf
Additional Drivers (jockey-kde)
Additional Drivers (jockey-gtk)

I have again tried to crash with Google Maps, but it doesn't seem to happen now.
And I'm encouraged to say, mystery solved?

---

### Post by wildmanne39 on 2011-09-10
Hi, give it some time and see how it goes I am reading the massive amount of log files you emailed me.
Also please post the results of this command:
```
lsmod | grep ati
```
Thank you

---

### Post by george5729 on 2011-09-11
lsmod | grep ati

Returns nothing... it's blank.

lsmod | grep radeon

$ lsmod | grep radeon
radeon                900494  1 
ttm                    65184  1 radeon
drm_kms_helper         40745  1 radeon
drm                   184164  3 radeon,ttm,drm_kms_helper
i2c_algo_bit           13184  2 radeon,ivtv


Thanks and kind regards

---

### Post by wildmanne39 on 2011-09-11
Hi, is it still working?

---

### Post by george5729 on 2011-09-13
It is working now in a more reliable fashion. The machine crashes less.
But it has crashed when I have over tasked the system.

I would like to know if the ubuntu 3.0 kernel is available?
(I understand 2.6.39 is already passed by this newer version)

---

### Post by wildmanne39 on 2011-09-13
Hi, yes it is available but it is still in testing phase, here is a link if you want to try it.
[http://ubuntuguide.net/how-to-install-linux-kernel-3-0-rc2-in-ubuntu-11-04-natty-narwhal](http://ubuntuguide.net/how-to-install-linux-kernel-3-0-rc2-in-ubuntu-11-04-natty-narwhal)

I am currently in the hospital on there wifi so it will be a few days until I am back on here, when I am feeling better.
Thank you

---

### Post by george5729 on 2011-09-14
Wildmanne,

Get well soon.

Kind regards,
George

---

