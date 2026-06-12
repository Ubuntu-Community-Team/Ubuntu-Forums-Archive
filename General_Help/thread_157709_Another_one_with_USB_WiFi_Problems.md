---
title: "Another one with USB WiFi Problems"
date: 2006-04-09
forum: General Help
---

### Post by Ferrat on 2006-04-09
Okej, this problem is OLD! I know but still can't get it to work.:-k  

I'm using 5.10 and have a D-LINK DWL-G132 (USB wireless network) and I can't get it installed on my Ubuntu, first of I tried the 64bit version but gave up on that since nothing was working so now I'm on a 32bit Ubuntu, easier true but still I'm having problems](*,) , I'm currently trying to minimize my use of Windows but first of I need to get Internet starting on linux. 

I used to have a CAT5 but due to changes I now only have my DWL-G132 USB network adapter, it works in Windows and I use dual boot so I can get files online just not get online when inside linux, now I need help. 

I've tried with Ndiswrapper (the one that comes with the dist) and I can install the drivers using 
```

holokauston@Rage:~/Desktop/ndiswrapper-1.13$ ndiswrapper -i NetA5AGU.inf
holokauston@Rage:~/Desktop/ndiswrapper-1.13$ ndiswrapper -i athfmwdl.inf

holokauston@Rage:~/Desktop/ndiswrapper-1.13$ ndiswrapper -l
Installed ndis drivers:
athfmwdl        driver present, hardware present
neta5agu        driver present, hardware present

```
but when running 
holokauston@Rage:~/Desktop/ndiswrapper-1.13$ modprobe ndiswrapper

It stalls, not the kernel but ndiswrapper, I get an error that it couldn't be loaded when looking in dmesg and I need to restart for Ubuntu to let go of the USB adapter (lsusb can't get to it and nothing else either that want to talk to my little USB WiFI for info)

```

[4295566.890000] Process loadndisdriver (pid: 10712, threadinfo=f7fd6000 task=f7 0d8aa0)
[4295566.890000] Stack: f7cb4000 f7d00000 f8df0a94 00000000 00000000 00000000 00 000000 f7c93220
[4295566.890000]        f7d00000 f8df0d35 f7c95800 df8dee80 f7c93000 ffffffed f6 0f8388 00000000
[4295566.890000]        f7d00000 f7cb4000 00180016 f8df0b30 00180016 f8df0b48 f8 d8ae82 f7fd7e40
[4295566.890000] Call Trace:
[4295566.890000]  [<f8d8ae82>] miniport_init+0x57/0x5b [ndiswrapper]
[4295566.890000]  [<f8d81878>] ndiswrapper_add_one_usb_dev+0x8f/0x154 [ndiswrapp er]
[4295566.890000]  [<f892f04f>] usb_probe_interface+0x49/0x60 [usbcore]
[4295566.890000]  [<c01ebfe6>] driver_probe_device+0x36/0x54
[4295566.890000]  [<c01ec0be>] driver_attach+0x39/0x6a
[4295566.890000]  [<c01ec444>] bus_add_driver+0x5e/0x80
[4295566.890000]  [<c01ec7a5>] driver_register+0x23/0x25
[4295566.890000]  [<f892f10d>] usb_register+0x42/0x87 [usbcore]
[4295566.890000]  [<f8d825e5>] register_devices+0x43a/0x4d2 [ndiswrapper]
[4295566.890000]  [<c019cb84>] copy_from_user+0x34/0x58
[4295566.890000]  [<f8d826b3>] wrapper_ioctl+0x36/0xaa [ndiswrapper]
[4295566.890000]  [<c0152fd8>] do_ioctl+0x48/0x4e
[4295566.890000]  [<c0153233>] vfs_ioctl+0x172/0x17f
[4295566.890000]  [<c0153286>] sys_ioctl+0x46/0x60
[4295566.890000]  [<c0102e9f>] sysenter_past_esp+0x54/0x75
[4295566.890000] Code: e0 08 0b c8 51 57 e8 0a 05 00 00 8b 0b 57 51 e8 91 08 00 00 85 c0 75 06 57 e8 d7 04 00 00 5f 5e 5b c2 08 00 cc 56 57 8b 7c 24 0c <8b> 07 6a 31 50 e8 40 04 00 00 8b f0 85 f6 74 71 8b 44 24 10 8b
[4295566.890000]  <3>ndiswrapper (wrapper_init:1534): loadndiswrapper failed (11 ); check system log for messages from 'loadndisdriver'
[4295566.904000] usbcore: deregistering driver ndiswrapper

```

And when I try to fix the new Ndiswrapper I get this if that is the problem? 
```

holokauston@Rage:~/Desktop/ndiswrapper-1.13$ make install
make -C driver install
make[1]: Entering directory `/home/holokauston/Desktop/ndiswrapper-1.13/driver'
Can't find kernel build files in /lib/modules/2.6.12-9-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/holokauston/Desktop/ndiswrapper-1.13/driver'
make: *** [install] Error 2
holokauston@Rage:~/Desktop/ndiswrapper-1.13$

```
But I don't know where to point it? :confused: 


Also DWL-G132 is using chipset Atheros, and that should mean that the MadWiFi drivers should work right? or atleast in theory according to what I understand, problem is this? 

First of I understand that Ubuntu already have MadWiFi but an older version so I need to uninstall that first, now I've read some texts on how to do this but they are somewhat obscure in the area (or so it seems to me) and then when using make I get the same problem as with ndiswrapper. 
```

holokauston@Rage:~/Desktop/MadWifi$ make install
/bin/sh: line 0: cd: /lib/modules/2.6.12-9-386/build: No such file or directory
Makefile.inc:95: *** /lib/modules/2.6.12-9-386/build is missing, please set KERNELPATH.  Stop.
holokauston@Rage:~/Desktop/MadWifi$

```

Also here are the outputs for lsusb (short version) and lshw
```

holokauston@Rage:~$ lsusb
Bus 005 Device 003: ID 2001:3a02 D-Link Corp. [hex]
Bus 005 Device 001: ID 0000:0000

```
```

holokauston@Rage:~$ sudo lshw -C generic
Password:
  *-generic UNCLAIMED
       physical id: 123
       bus info: parisc@123
  *-usb UNCLAIMED
       description: Generic USB device
       product: USB WLAN Device
       vendor: Atheros Communications Inc
       physical id: 4
       bus info: usb@5:4
       version: 0.01
       serial: 1.0
       capabilities: usb-2.00
       configuration: maxpower=500mA speed=480.0MB/s

```

Remember I can't use internet inside linux but can get ziped files ect to it easy, anyone got any smart ideas? :)

---

### Post by dpicker on 2006-04-09
Run:

```
sudo apt-get install linux-headers-2.6.12-9-386 build-essential
```

(You dont need the internet for those commands)

Then you should be able to compile both ndiswrapper and madwifi.

---

### Post by Ferrat on 2006-04-09
Ok thx =) I'll try that

---

### Post by Ferrat on 2006-04-09
Nope, didn't work, well the compiler worked thx =) but still no working network, I don't really get any error just works and then nothing >_<


Tried compiling MadWiFi drivers too, well they first said, you got old drivers do you want to remove them first? (I said yes) 

Then I got this when running 

```

holokauston@Rage:~/Desktop/mad$ sudo make install
sh scripts/find-madwifi-modules.sh /lib/modules/2.6.12-9-386
for i in ./ath_hal ./net80211 ath_rate/sample ./ath; do \
        make -C $i install || exit 1; \
done
make[1]: Entering directory `/home/holokauston/Desktop/mad/ath_hal'
test -d //lib/modules/2.6.12-9-386/net || mkdir -p //lib/modules/2.6.12-9-386/net
strip -S ath_hal.ko
strip: 'ath_hal.ko': No such file
cp ath_hal.ko //lib/modules/2.6.12-9-386/net
cp: cannot stat `ath_hal.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/holokauston/Desktop/mad/ath_hal'
make: *** [install-modules] Error 1

```

Any ideas? 

tried repeating the ndiswrapper install and compiling ect about 5times same thing every time and can't find anything wrong :(

---

### Post by Ferrat on 2006-04-10
*bump* 

Anyone got any idea?

---

### Post by Ferrat on 2006-04-10
Ok been reading a bit and looks like installing Dapper might help since it uses newer versions ect? 

As I Understand Dapper for ex. uses a later version of MadWiFi and that version might be able to handle my DWL-G132 and a newer version of ndiswrapper that might be used incase the first option doesn't work?

And from what I hear Dapper is close to beta and pretty stable? don't mind the harder work installing thing, like the challenge just need my Internet working so I got a fighting chance ^^

---

### Post by MenZa on 2006-04-10
[QUOTE=Ferrat]From what I hear Dapper is close to beta and pretty stable?^[/QUOTE]

Stable enough for my needs :)

---

### Post by Ferrat on 2006-04-10
Great, I'll give it a try worst thing that can happen is I need to reinstall something ^^ 

Only real goals right now it get that darn USB WiFi Working and wine/cedega Dungeons and Dragons Online and my banksecurity program, after that I don't need Windows for much at all =)

---

### Post by Ferrat on 2006-04-10
YEAH! Success and way easy installing D-LINK DWL-G132 USB WiFi on Dapper, just more or less out of the box, just install ndiswrapper that came with the disp, then use ndisgtk_0.5-1ubuntu1_all.deb for ndisgtk, download the latest drivers from d-link.com and install, up and running in no time :) 

Now I just need to fix the resolution ^^ 640x400 is a little to big ^^

---

