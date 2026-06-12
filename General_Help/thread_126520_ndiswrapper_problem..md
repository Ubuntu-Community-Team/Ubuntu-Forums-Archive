---
title: "ndiswrapper problem."
date: 2006-02-06
forum: General Help
---

### Post by ** Andy ** on 2006-02-06
Would someone help me to solve these problems?

I have this problem with ndiswrapper 1.1. I can install it and install the driver for my U.S.B. wireless receiver. That's fine. When it comes to modprobe ndiswrapper, though, it fails. It gives me this output:




[4295306.173000] ndiswrapper version 1.1 loaded (preempt=no,smp=no)
[4295306.234000] ndiswrapper: driver rt73 (Belkin,08/02/2005, 1.00.00.0000) loaded
[4295306.299000] Unable to handle kernel NULL pointer dereference at virtual address 00000000
[4295306.299000]  printing eip:
[4295306.299000] dec5cad3
[4295306.299000] *pde = 00000000
[4295306.299000] Oops: 0002 [#1]
[4295306.299000] Modules linked in: ndiswrapper ipv6 rfcomm l2cap bluetooth speedstep_lib cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sony_acpi pcc_acpi hotkey dev_acpi i2c_acpi_ec i2c_core button battery container ac tsdev pcspkr rtc snd_intel8x0 snd_ac97_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd soundcore snd_page_alloc pci_hotplug sis_agp agpgart nls_cp437 ntfs dm_mod evdev psmouse mousedev parport_pc lp parport md ext3 jbd thermal processor fan usbhid sis900 mii ehci_hcd ohci_hcd usbcore ide_cd cdrom ide_disk ide_generic sata_sis libata scsi_mod sis5513 ide_core unix vesafb capability commoncap vga16fb vgastate softcursor cfbimgblt cfbfillrect cfbcopyarea fbcon tileblit font bitblit
[4295306.299000] CPU:    0
[4295306.299000] EIP:    0060:[<dec5cad3>]    Tainted: P      VLI
[4295306.299000] EFLAGS: 00010246   (2.6.12-9-386)
[4295306.299000] EIP is at 0xdec5cad3
[4295306.299000] eax: 00000000   ebx: d32df000   ecx: 00000000   edx: 00000000
[4295306.299000] esi: ffffffed   edi: d193e400   ebp: cd72fd7c   esp: cd72fd74
[4295306.299000] ds: 007b   es: 007b   ss: 0068
[4295306.299000] Process loadndisdriver (pid: 7242, threadinfo=cd72e000 task=d203e520)
[4295306.299000] Stack: 00000000 00000000 cd72fdfc dec5b1eb 00000000 0000000c cfc8c8c0 00000001
[4295306.299000]        dec31aa7 00000000 00000000 00000000 dec9f5b1 00000000 00000000 00000020
[4295306.299000]        dec9f630 ffffffed 00000000 dec3479d dec9f630 d32df220 d32df000 dec5d1a4
[4295306.299000] Call Trace:
[4295306.299000]  [<dec31aa7>] wrap_kmalloc+0x3d/0x78 [ndiswrapper]
[4295306.299000]  [<dec3479d>] NdisMInitializeTimer+0xf/0x2c [ndiswrapper]
[4295306.299000]  [<dec39e82>] miniport_init+0x57/0x5b [ndiswrapper]
[4295306.299000]  [<dec30878>] ndiswrapper_add_one_usb_dev+0x8f/0x154 [ndiswrapper]
[4295306.299000]  [<de91a04f>] usb_probe_interface+0x49/0x60 [usbcore]
[4295306.299000]  [<c01ebfe6>] driver_probe_device+0x36/0x54
[4295306.299000]  [<c01ec0be>] driver_attach+0x39/0x6a
[4295306.299000]  [<c01ec444>] bus_add_driver+0x5e/0x80
[4295306.299000]  [<c01ec7a5>] driver_register+0x23/0x25
[4295306.299000]  [<de91a10d>] usb_register+0x42/0x87 [usbcore]
[4295306.299000]  [<dec315e5>] register_devices+0x43a/0x4d2 [ndiswrapper]
[4295306.299000]  [<c019cb84>] copy_from_user+0x34/0x58
[4295306.299000]  [<dec316b3>] wrapper_ioctl+0x36/0xaa [ndiswrapper]
[4295306.299000]  [<c0152fd8>] do_ioctl+0x48/0x4e
[4295306.299000]  [<c0153233>] vfs_ioctl+0x172/0x17f
[4295306.299000]  [<c0153286>] sys_ioctl+0x46/0x60
[4295306.299000]  [<c0102e9f>] sysenter_past_esp+0x54/0x75
[4295306.299000] Code: fc 00 00 00 00 8b 45 08 89 45 f8 c7 45 fc 00 00 00 00 eb 09 8b 4d fc 83 c1 01 89 4d fc 8b 55 fc 3b 55 0c 73 0b 8b 45 f8 03 45 fc <c6> 00 00 eb e4 8b e5 5d c2 08 00 cc cc 55 8b ec 83 ec 0c 8b 45
[4295306.299000]  <3>ndiswrapper (wrapper_init:1534): loadndiswrapper failed (11); check system log for messages from 'loadndisdriver'
[4295306.305000] usbcore: deregistering driver ndiswrapper




I thought that it might be because it is an old version of ndis, so I downloaded 1.8. I can't install it, though. It says that it can't find the kernel modules and to give the path to them. It mentions something about KRSC, I think. You'll have to excuse me, as I'm writing this in XP and I don't have the exact output from the command line.

Is anyone able to tell me how to fix either the problem with 1.1 or tell me the exact command to use in order to install 1.8 and try with that instead? I presume that it's 'make install <path to kernel modules>', or something like that.

---

### Post by az on 2006-02-06
[QUOTE=** Andy **][4295306.234000] ndiswrapper: driver rt73 (Belkin,08/02/2005, 1.00.00.0000) loaded
[4295306.299000] Unable to handle kernel NULL pointer dereference at virtual address 00000000
[[/QUOTE]


The problem is with the windows driver you are trying to use.  Look at the ndiswrapper wiki page for the most recent version for your card.

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

Nevermind recompiling ndiswrapper1.8

---

### Post by ** Andy ** on 2006-02-07
Hello. Thanks for the reply. It's a Belkin F5D7050 U.S.B. adapter. I've read the Wiki instructions and they say to use the driver on the C.D., which I have done. There are two folders on the C.D., one for Win95 and one for XP. I have used the .inf and .sys files from the XP folder (on the C.D.). The drivers available from the Belkin site are older than those on the C.D., but I'll try them and report back.

Thanks.

---

### Post by JustRandomName on 2006-02-10
Hi Andy,

I just bought the same card of you today, and I am also having problems getting it working.

After some research I have found that you need to look right at the bottom of the box which your card came in, and look for a little sticker with the version number on it (about 5mm x 25mm).

If you have a version 3000 (which I do) I think you are out of luck.

Because the chip which it uses is the rt73

This hasn't been open sourced by Ralink (so serial monkey drivers won't work)however there is some precompiled divers at

[http://www.ralinktech.com/supp-1.htm](http://www.ralinktech.com/supp-1.htm)

Unforunatly they are not up to date so it means that we would have to use an old kernel. I am not willing to do this so I am going to have another go with ndiswrapper.

I am going to try each of the drivers listed here:

[http://www.belkin.com/support/download.asp?query=f5d7050&lang=1&mode=&Search=Search](http://www.belkin.com/support/download.asp?query=f5d7050&lang=1&mode=&Search=Search)

I will report back if I have any success, but you might want to try the same.

---

### Post by JustRandomName on 2006-02-10
Success!

It turns out that you need to be using ndiswrapper 1.8. I found this in the darkest corner of the internet:
[http://ask.slashdot.org/comments.pl?sid=174875&threshold=-1&commentsort=0&mode=thread&cid=14545328](http://ask.slashdot.org/comments.pl?sid=174875&threshold=-1&commentsort=0&mode=thread&cid=14545328)

Anyway... I followed this guide to install ndiswrapper 1.8 (haven't tried 1.9 yet)

[http://www.ubuntuforums.org/showthread.php?t=104539](http://www.ubuntuforums.org/showthread.php?t=104539)

Then I installled the XP drivers found the disc that came with the card. 

$ sudo ndiswrapper -i rt73.inf
$ sudo ndiswrapper -l

Check that it says the drivers AND hardware are present.

$ sudo ndiswrapper -m
$ sudo modprobe ndiswrapper

$ sudo ifup wlan0

It should be noted that I already had this in /etc/networking/interfaces


iface wlan0 inet dhcp
wireless-essid YOUR_ROUTER_NAME
wireless-key YOUR_ROUTER_KEY
wireless-mode Managed
auto wlan0


If not then add it in and try sudo ifup wlan0 again.

---

### Post by ** Andy ** on 2006-02-10
Cheers, you're a saint. :-) I have the rt73, you're correct. I'm also using 1.1, not 1.8. The problem is that I cannot install 1.8. I get an error saying:

Can't find kernel sources in /lib/modules/2.6.12-9-386/build;
 give the path to kernel sources with KSRC=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/andy/Personal/programs - downloads/ndiswrapper/ndiswrapper-1.8/driver'
make: *** [install] Error 2

As long as I can get around this problem, I should be able to follow your lead. Fingers crossed!

Thanks for letting me know. It's very much appreciated.

---

### Post by JustRandomName on 2006-02-10
Are you sure that you have the kernel headers installed?

If not, then try:

sudo apt-get install linux-headers-`uname -r`

---

### Post by JustRandomName on 2006-02-10
I should also mention that this my system hasn't been very stable since I have installed ndiswrapper.

I have had two freeze's so far today (pretty sure that it is ndiswrapper, although I can't find any evidence in the logs).

I also can't get the network to connect on boot. I have added `ndiswrapper' to the modules file, and when boot gets to "Configuring Network Devices" it seems to hand. I left it for over 5 minutes and nothing so I ctrl+c out of it. The strange thing is the card flash's away as if it is working.

I haven't tried the stability of the connection under heavy loads yet, this will have to wait until tomorrow (4AM here).

If you manage to solve any of these issues please tell us ;)

---

### Post by ** Andy ** on 2006-02-12
I had the headers installed, but it must have gone a bit mad when I messed about with installing 1.8. I reinstalled the headers and now it seems fine. I don't get that error any longer. I get one saying 'gcc-3.4 Command not found', instead! I have gcc-4.0 installed, so that one makes no sense at all. I suppose that it's back to the search engine for a solution... :-k

---

### Post by JustRandomName on 2006-02-12
Yeah I remember when I had that problem. This is a great how-to: [http://ubuntuforums.org/showthread.php?t=79896](http://ubuntuforums.org/showthread.php?t=79896)

The ndiswrapper doesn't work well under heavy strain :( I keep getting hard lock ups

---

### Post by SWAT on 2006-02-12
Uhm, version 1.1 of ndiswrapper is really not the newest one. [I have a Broadcom WLAN chipset working really well with Ndiswrapper](http://www.zwhlug.nl/content/ndiswrapper_how_to_install_and_compile_ndiswrapper), I use it everyday to connect to my WEP secured school WLAN. 
Compiling/Installing Ndiswrapper can be a pain, but that's usually because you don't have the linux source (of your kernel) installed and configured.

---

### Post by az on 2006-02-12
[QUOTE=SWAT]Uhm, version 1.1 of ndiswrapper is really not the newest one. [I have a Broadcom WLAN chipset working really well with Ndiswrapper](http://www.zwhlug.nl/content/ndiswrapper_how_to_install_and_compile_ndiswrapper), I use it everyday to connect to my WEP secured school WLAN. 
Compiling/Installing Ndiswrapper can be a pain, but that's usually because you don't have the linux source (of your kernel) installed and configured.[/QUOTE]

The broadcom chipset has worked since before ndiswrapper 1.1.  The version that ships with breezy works fine.

You do not need to recompile it.  You usually need to get the latest version of the windows driver, though.  It is clearly stated in the ndiswrapper documentation that the windows drivers that ship with the device can be too old.


And to recompile something for your kernel, all you need are the linux-headers.  Use synaptic to search for linux-headers and install the package that matches you installed linux-image package.  Using the whole kernel source is a waste of time, bandwidth and disk space.  Not to mention you have to configure it to match your running kernel and compile it.  Just install the linux-headers package and you are done.

---

### Post by ** Andy ** on 2006-02-12
I had that problem with Opera on my previous system and computer. How fat is your o.s., exactly? I have a new computer and the latest release of Kubuntu, so I might have better luck. What about ndis 1.9? Have you tried that yet?

---

### Post by JustRandomName on 2006-02-16
I had a quick try with 1.9 and couldn't get it too work.

The 1.8 is super unstable, it may be because I am using smp so I will try compiling again with just a non-smp kernel.

---

### Post by JustRandomName on 2006-02-16
Hi,

How is your problem going?

I *think* I have solved the stability problem check for details 

[http://ubuntuforums.org/showthread.php?t=128323](http://ubuntuforums.org/showthread.php?t=128323)

I may be talking too soon (only an hour so far), the summary is use ndiswrapper 1.10 and the drivers on the CD.

---

### Post by ** Andy ** on 2006-02-18
I'm still trying to install gcc-3.4. I had a quick go a few days ago, but it didn't work. I deviated from the instructions a little, so that's probably why! I'll give 1.9 a miss, then. Use 1.1 and the drivers on the C.D.? Hmmm, funny, that's exactly the reason that I posted to begin with. It didn't work for me. Ndis wouldn't load with 'modprobe ndiswrapper'. I wonder what you did that I didn't. I followed the instructions on Wiki to the letter.

This is supremely annoying!:-k

---

### Post by ** Andy ** on 2006-02-20
I found this on a forum:

'Also, it seems that the ndiswrapper module is not showing up, make sure it's in /lib/modules/<your kernel version>/extra , should be called ndiswrapper.ko.'

I looked and ran a search - no ndiswrapper.ko to be found. It's no wonder my ndis won't even load! If I manage to get hold of someone else's ndiswrapper.ko for 1.1 and copied it to the appropriate folder, do you think that it would then work, or would it need to be created by the ndiswrapper installer?

---

### Post by JustRandomName on 2006-02-27
no use 1.10 (one point ten) drivers not 1.1 (one point one)

I really doubt copying the .ko would work

It is really simple to get it working, just follow the guides that I have mentioned (if you get stuck on one point then tell us! don't just plow through to the end of the guide)

The drivers are SUPER STABLE ... I have had a heavy load on it for up to 72 hours (it probably would of carried on but I had to reboot the router due to changing some settings)

---

### Post by ** Andy ** on 2006-03-16
Well, it's been a while, but I have finally got around to re-installing Breezy 5.10 and I have ndiswrapper working!:) 

I did this:

* In Adept I installed kernel headers, ndisutils and gcc 4.
* Followed the instructions here [http://ubuntuforums.org/showthread.php?t=79896]("http://ubuntuforums.org/showthread.php?t=79896") to install gcc-3.4.
* Followed the Wiki for ndiswrapper to install ndiswrapper 1.8, except for not performing make 'distclean'. [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation")
* Wrapped the drivers from my C.D. using the instructions in the Wiki and loaded the module.

All is now up and running! \\:D/  It's a shame that there is no instant W.P.A. support. There's some information about it here [http://ndiswrapper.sourceforge.net/mediawiki/index.php/WPA]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/WPA"), if anyone desperately wants to use W.P.A. I can't be fussed after spending so long trying to get ndiswrapper working, so I'll just use W.E.P.

Thank-you to everyone who lent a hand.

---

