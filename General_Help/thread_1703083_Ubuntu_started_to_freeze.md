---
title: "Ubuntu started to freeze"
date: 2011-03-08
forum: General Help
---

### Post by rkm.sbc on 2011-03-08
Hello guys, i installed ubuntu few days ago, all seemed to be working so i have started building and customizing my workshop. Yesterday my ubuntu started to freeze. I just cant move mouse nor do anything else, if any music is being played it starts to loop one second of it, only hard reboot helps. Sometimes screens gets distorted too (looks like a c64 while loading data from a tape lol). I dont think its a hardware problem cause i was running winxp on this machine for few years without any problems.  I went to read logs hoping to find what makes my ubuntu to freeze but tbh i dont have any idea which error can cause a system crash. I went through all logs with CTRL+F for 'error' and heres what i found:

xorg.log:
```
[    57.041] Warning: Xalloc: requesting unpleasantly large amount of memory: 0 bytes.
``` that1 above is being repeated few times in a row

more in xorg.log
```
[    43.217] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
```
more in xorg.log
```
[    31.001] (EE) NVIDIA(GPU-0): Your GeForce 7600 GS graphics card does not have the necessary
[    31.001] (EE) NVIDIA(GPU-0):     external power cables attached; X will not start unless
[    31.001] (EE) NVIDIA(GPU-0):     this is rectified.  Please shut down your computer, open
[    31.001] (EE) NVIDIA(GPU-0):     its case, and attach the appropriate power connectors. 
[    31.001] (EE) NVIDIA(GPU-0):     Your video card may have multiple power connectors.  If
[    31.001] (EE) NVIDIA(GPU-0):     so, each must be attached to a separate power cable. 
[    31.001] (EE) NVIDIA(GPU-0):     Please see the documentation provided with your video card
[    31.002] (EE) NVIDIA(GPU-0):     for more details.  If you think you have received this
[    31.002] (EE) NVIDIA(GPU-0):     message in error, you may specify the
[    31.002] (EE) NVIDIA(GPU-0):     "NoPowerConnectorCheck" X configuration option in the
[    31.002] (EE) NVIDIA(GPU-0):     Screen section of your X config file.
[    31.050] (II) UnloadModule: "nvidia"
[    31.050] (II) UnloadModule: "wfb"
[    31.050] (II) UnloadModule: "fb"
[    31.050] (EE) Screen(s) found, but none have a usable configuration.
[    31.050] 
Fatal server error:
[    31.050] no screens found
```
All cables are connected.

dmesg & dmesg.log
```
[    3.316021] usb 2-4: new full speed USB device using ohci_hcd and address 4
[    3.724064] usb 2-4: device not accepting address 4, error -62
```
this one appears in kern.log also

kern.log
```
Mar  9 00:19:20 above-rainbow kernel: [  795.953847] Call Trace:
Mar  9 00:19:20 above-rainbow kernel: [  795.953855]  [<c02171ec>] ? filp_close+0x3c/0x80
Mar  9 00:19:20 above-rainbow kernel: [  795.953860]  [<c014d04b>] ? put_files_struct+0x6b/0xb0
Mar  9 00:19:20 above-rainbow kernel: [  795.953864]  [<c014d0d8>] ? exit_files+0x48/0x60
Mar  9 00:19:20 above-rainbow kernel: [  795.953868]  [<c014f3c4>] ? do_exit+0x134/0x340
Mar  9 00:19:20 above-rainbow kernel: [  795.953875]  [<c05c81a3>] ? printk+0x2d/0x32
Mar  9 00:19:20 above-rainbow kernel: [  795.953880]  [<c05cc0e5>] ? oops_end+0x95/0xd0
Mar  9 00:19:20 above-rainbow kernel: [  795.953886]  [<c012df44>] ? no_context+0xc4/0xe0
Mar  9 00:19:20 above-rainbow kernel: [  795.953891]  [<c012dff0>] ? __bad_area_nosemaphore+0x90/0x130
Mar  9 00:19:20 above-rainbow kernel: [  795.953896]  [<c0571675>] ? unix_stream_recvmsg+0x425/0x4f0
Mar  9 00:19:20 above-rainbow kernel: [  795.953901]  [<c012e0f0>] ? bad_area+0x40/0x50
Mar  9 00:19:20 above-rainbow kernel: [  795.953905]  [<c05ce38f>] ? do_page_fault+0x42f/0x440
Mar  9 00:19:20 above-rainbow kernel: [  795.953911]  [<c04e88f8>] ? sock_aio_read+0x138/0x140
Mar  9 00:19:20 above-rainbow kernel: [  795.953916]  [<c05cdf60>] ? do_page_fault+0x0/0x440
Mar  9 00:19:20 above-rainbow kernel: [  795.953920]  [<c05cb4d7>] ? error_code+0x73/0x78
Mar  9 00:40:07 above-rainbow kernel: [ 1199.441894] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar  9 00:40:07 above-rainbow kernel: [ 1199.441906] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
Mar  9 00:40:07 above-rainbow kernel: [ 1199.441915] sr 0:0:1:0: [sr0] Add. Sense: Illegal mode for this track
Mar  9 00:40:07 above-rainbow kernel: [ 1199.441926] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
Mar  9 00:40:07 above-rainbow kernel: [ 1199.441942] end_request: I/O error, dev sr0, sector 0
Mar  9 00:40:07 above-rainbow kernel: [ 1199.441948] quiet_error: 6 callbacks suppressed
Mar  9 00:40:07 above-rainbow kernel: [ 1199.441954] Buffer I/O error on device sr0, logical block 0
Mar  9 00:40:07 above-rainbow kernel: [ 1199.441960] Buffer I/O error on device sr0, logical block 1
```

sys.log
```
Mar  9 00:20:29 above-rainbow NetworkManager[902]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Mar  9 00:20:57 above-rainbow NetworkManager[902]: <error> [1299626457.274810] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Mar  9 00:20:57 above-rainbow NetworkManager[902]: <error> [1299626457.330022] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
```

Are any of those critical? Last time my system freezed around 00:06 of my localtime, i was unable to find any errors around that time. Those freezes seem to apper randomly, i dont remember doing anything special when one of them occured.

Some info about hardware:
Amd Athlon 2800+ with 1gb 400 mhz ram of unknown manufacturer
Nvidia 7600 GS, Western Digital hdd with 40gb capacity & sound blaster audigy (II i believe). Dont remember the motherboard manufacturer, i thnik it has something to do with realtek. 

Any help? Advice? Any more specific informations that i should probide?
Thanks in advance, sbc.

---

### Post by kris kincaid on 2011-03-10
Same thing is happening to me. I disabled the Nvidia driver, now no more problems. It's not a great solution, but now I can do work without the computer freezing.

Hopefully somebody chimes in here

---

### Post by rkm.sbc on 2011-03-11
Can you tell me what is your graphics card and other system spec? Also which version of nvidia drivers you where using before you diabled it ?

---

### Post by The End of The World on 2011-03-11
Mine's freezing too, though I have no nvidia drivers. Perhaps it's the xorg update that was a few days ago? Maybe theres a way to downgrade to the previous version?

---

### Post by kris kincaid on 2011-03-12
My video card is a [GIGABYTE GV-N460OC-1GI]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814125333") and the processor is an [AMD Phenom II X6 1090T]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103849") I used 10.10 AMD64 and it happened, so I updated to an 11.04 AMD64 beta and it still happened. I'm not really sure what driver I was using, whatever was installed through the "Additional Drivers" program. I'm sure it's whatever is current in 10.10. I'm not sure what generic driver I'm currently using. How do I check?

My system is fairly new, so I thought it was a hardware issue. I got the system together and it ran fine for about 2 weeks, then all the sudden (Likely after an update) it started freezing. After my ham fisted troubleshooting methods had screwed up the system so bad that it wouldn't boot, I did a fresh reinstall of 11.04. Everything was working fine for a night, then the next day I enabled the "Additional Drivers" for the Nvidia video card and within a minute I got the freezing issue again. I disabled the Nvidia driver and so far the system has been up for 4 days straight with zero issues.

If you need anything else, let me know and I'll try to help with info as best I can. :)




> **rkm.sbc said:**
> Can you tell me what is your graphics card and other system spec? Also which version of nvidia drivers you where using before you diabled it ?

---

### Post by kris kincaid on 2011-03-12
This guy pretty much verified to me that it was the Nvidia driver, but honestly I have no idea what the true culprit is. I just know whats working now.

[http://edtake.wordpress.com/2011/02/13/ubuntu-nvidia-driver-random-freeze/](http://edtake.wordpress.com/2011/02/13/ubuntu-nvidia-driver-random-freeze/)

---

### Post by The End of The World on 2011-03-13
While not having any nvidia card in my laptop, a thing that's worked for me is installing gconf-cleaner.
```
sudo apt-get install gconf-cleaner
```I had a lot of gconf issues, perhaps xorg was one of them. Anyway, it's fixed now, so if you arent on a computer with nvidia, it's worth a try. Note that program preferences will be reset - wifi passwords, some application settings (i lost docky's preferences, anyway).
Hope this works for you!


(I also removed compiz's extra plug-ins pack, the community one. I don't know if that helped, but yeah)

---

### Post by rkm.sbc on 2011-03-15
Ok thanks for your replies folks, 5 minutes ago ive disabled Nvidia drivers lets see whats gonna be my uptime now. I have preapred few others distros to install just in case if its not nividia driver issue.

---

