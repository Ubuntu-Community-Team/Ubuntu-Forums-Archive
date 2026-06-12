---
title: "new linux 'compatible' usb video adapter is not working."
date: 2011-07-15
forum: General Help
---

### Post by Cammaaron on 2011-07-15
Just today, I got my UGA video adapter in, when purchasing it I saw on its requirements that is showed it had linux support. 

However, when plugged it in and restarting no image but the default  green image was shown. All wires are check and are plugged in.

However, I am not seeing on the computer monitor and no 2nd monitor is  found on the monitor settings. Also I would like to note that according  to a little research, is that the usb video adapter uses displaylink.

I am using Ubuntu 11.04, classic ubuntu and 2D unity desktop.
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=11051392") 		 		  	 	 	 	 		  		 			 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=11051392")

---

### Post by LowSky on 2011-07-15
could you list the model that you purchased.. what are the terminal results of the command
```
lsusb
```

---

### Post by Cammaaron on 2011-07-15
It gives
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 004: ID 0cf3:3005 Atheros Communications, Inc. 
Bus 004 Device 002: ID 0eef:725e D-WAV Scientific Co., Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 021: ID 17e9:0198 Newnham Research 
Bus 001 Device 020: ID 0572:1412 Conexant Systems (Rockwell), Inc. 
Bus 001 Device 019: ID 046d:c31c Logitech, Inc. 
Bus 001 Device 018: ID 046d:c05a Logitech, Inc. Optical Mouse M90
Bus 001 Device 017: ID 03f0:1d04 Hewlett-Packard 
Bus 001 Device 016: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 015: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 014: ID 413c:a502 Dell Computer Corp. 
Bus 001 Device 003: ID 174f:1423 Syntek 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```I believe it is Newnham Research as it is the only one that disappears when unplugged.

model WS-UG12D1

S/N:5242001200287

also found this on dmesg

> [16705.880116] usb 1-2: new high speed USB device using ehci_hcd and address 22
[16706.017575] udlfb: DisplayLink WS Tech USB-DVI - serial #527752
[16706.017593] udlfb: vid_17e9&pid_0198&rev_0129 driver's dlfb_data struct at cc8fd000
[16706.017606] udlfb: console enable=0
[16706.017614] udlfb: fb_defio enable=0
[16706.017842] udlfb: vendor descriptor length:23 data:23 5f 01 0021 00 04 04 07 00 01
[16706.017857] udlfb: DL chip limited to 1500000 pixel modes
[16706.018161] udlfb: allocated 4 65024 byte urbs
[16706.102287] udlfb: 1366x768 valid mode
[16706.102299] udlfb: 1360x768 valid mode
[16706.102308] udlfb: 720x400 valid mode
[16706.102315] udlfb: 640x480 valid mode
[16706.102322] udlfb: 640x480 valid mode
[16706.102329] udlfb: 640x480 valid mode
[16706.102337] udlfb: 640x480 valid mode
[16706.102344] udlfb: 800x600 valid mode
[16706.102352] udlfb: 800x600 valid mode
[16706.102359] udlfb: 800x600 valid mode
[16706.102366] udlfb: 800x600 valid mode
[16706.102374] udlfb: 832x624 valid mode
[16706.102381] udlfb: 1024x768 valid mode
[16706.102389] udlfb: 1024x768 valid mode
[16706.102396] udlfb: 1024x768 valid mode
[16706.102404] udlfb: 640x640 valid mode
[16706.102411] udlfb: 1024x768 valid mode
[16706.102420] udlfb: Reallocating framebuffer. Addresses will change!
[16706.105772] udlfb: 1366x768 valid mode
[16706.105788] udlfb: set_par mode 1366x768
[16706.113733] udlfb: DisplayLink USB device /dev/fb1 attached. 1366x768 resolution. Using 4104K framebuffer memory


---

### Post by LowSky on 2011-07-16
[http://www.win-star.com/eshop/article.php?id=24](http://www.win-star.com/eshop/article.php?id=24)
```
sudo apt-get install libusb-dev
```

Plug in a DisplayLink USB device

To start the build process, open a shell prompt and run

```
./configure && sudo make install && make check
```

"Make check" will do some basic drawing on one of the attached DisplayLink devices.

Please see the README in the distribution for more details.

---

### Post by Cammaaron on 2011-07-16
That did not work in a way I wanted it to.

I tried the make check first, but did not work. Disconnect and then reconnect and did cause the make check test images appear on the external monitor.

However I am still unable on making it extend my desktop. Also, what readme?

---

### Post by LowSky on 2011-07-16
Everything I wronte came from that link provided, I guess I didn't copy it completley:

[http://www.win-star.com/eshop/article.php?id=24](http://www.win-star.com/eshop/article.php?id=24)

---

### Post by Cammaaron on 2011-07-16
Where is the readme on the link?

---

### Post by Cammaaron on 2011-07-17
I found a blog posting about someone who got a usb video adapter suing displaylink working.

According to him, he said he used an Xorg config file to make it work.
[http://mulchman.org/blog/?tag=displaylink](http://mulchman.org/blog/?tag=displaylink)

However the operating system was for ubuntu 9.10.
So I just need to know how do I get the information to put in for my original settings?

Where do I put the Xorg config file?

And is there anything else I might need to do that has change from 9.10 that you can tell from that information.

---

