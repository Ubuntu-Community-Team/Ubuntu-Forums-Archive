---
title: "need help"
date: 2012-03-22
forum: General Help
---

### Post by jamesdavis111 on 2012-03-22
i have gave up on ubuntu so i want to switch to a trial of windows 7 can someone tell me how to totally uninstall ubuntu to get my windows 7 trial to work (ubuntu is the only os. there is no dualboot) any help?

---

### Post by PhantomTurtle on 2012-03-22
You can just delete and overwrite you Ubuntu partitions with the Windows Installer.

See Here if you want more help: [http://pcsupport.about.com/od/operatingsystems/ss/windows-7-clean-install-part-1_11.htm]("http://pcsupport.about.com/od/operatingsystems/ss/windows-7-clean-install-part-1_11.htm")(there are pictures).

---

### Post by jamesdavis111 on 2012-03-22
[B][SIZE=3]every time i try to run the disk i get this error 
[/SIZE][/B]

**[SIZE=3]"[/SIZE]windows has encountered a problem communicating with a device connected to your computer"**

[SIZE=4]it only does it for that one disk any advice?[/SIZE]

---

### Post by wildmanne39 on 2012-03-22
Hi, I suggest using the livecd then run gparted and unmount your hard drive then reformat the drive to NTFS and make it a primary partition and windows should install then.
Thanks

---

### Post by jamesdavis111 on 2012-03-22
[SIZE=4]i havent got a live is there any other way to just wipe the harddrive clean?[/SIZE]

---

### Post by wildmanne39 on 2012-03-22
Hi, please use normal fonts.

How did you install ubuntu?

You might be able to use the windows disc but I do not think it will see the drive.
Thanks

---

### Post by jamesdavis111 on 2012-03-22
yea sorry about that i ran a burnt ubuntu disk over the pc it said install to harddrive so i did an it erased everything other then ubuntu would you know what the problem is

---

### Post by wildmanne39 on 2012-03-22
Hi, so did you have windows on this computer before you installed ubuntu? and you just want to install it again correct? or do you want to have both now?

If you had windows it is possible it is still there and just not showing in the grub menu.
Thanks

---

### Post by jamesdavis111 on 2012-03-22
yes but the windows 7 had a total melt down so i had to use ubuntu to get all my stuff off the pc is there any way to just whip the total harddrive in trying to run a trial disk is all

---

### Post by wildmanne39 on 2012-03-22
Hi, you can try this free windows partition program it is suppose to be pretty good.
[http://www.partition-tool.com/](http://www.partition-tool.com/)
Thanks

---

### Post by jamesdavis111 on 2012-03-22
ok so if i dont install a new version of windows 7 is there anyway you can help me set up a netgear wna3100 usb wireless adapter i cant get it to install it says that the driver is there an the hardware it lights up just wont show that there are any connections present

---

### Post by wildmanne39 on 2012-03-22
Hi, that is possible and if I can not I will get someone who can.

Make sure your wireless adapter is plugged in then please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod

```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by jamesdavis111 on 2012-03-22
```

```#james@james-desktop:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"
Linux james-desktop 2.6.32-38-generic #83-Ubuntu SMP Wed Jan 4 11:13:04 UTC 2012 i686 GNU/Linux

james@james-desktop:~$ lspci -nnk | grep -iA2 net
00:07.0 Bridge [0680]: nVidia Corporation MCP61 Ethernet [10de:03ef] (rev a2)
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

james@james-desktop:~$ lsusb
Bus 002 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 002 Device 002: ID 15d9:0a4c Dexon 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0846:9020 NetGear, Inc. 
Bus 001 Device 002: ID 0644:0200 TEAC Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

james@james-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

james@james-desktop:~$ rfkill list all(i ran it it returned nothing)


james@james-desktop:~$ lsusb
Bus 002 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 002 Device 002: ID 15d9:0a4c Dexon 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0846:9020 NetGear, Inc. 
Bus 001 Device 002: ID 0644:0200 TEAC Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
james@james-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

james@james-desktop:~$ rfkill list all
james@james-desktop:~$ sudo rfkill list all
[sudo] password for james: 
james@james-desktop:~$ lsmod
Module                  Size  Used by
ndiswrapper           184677  0 
snd_hda_codec_realtek   203440  1 
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_mid  i_event
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi  ,snd_seq
nvidia               9961216  42 
snd                    54244  16  snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,   snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_se   q_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
dell_wmi                1793  0 
dcdbas                  5422  0 
lp                      7028  0 
agpgart                31724  1 nvidia
vga16fb                11385  1 
vgastate                8961  1 vga16fb
psmouse                63677  0 
serio_raw               3978  0 
k8temp                  3152  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
i2c_nforce2             5199  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
usb_storage            40033  0 
pata_amd                8766  0 
forcedeth              49556  0 
sata_nv                19376  2

---

### Post by wildmanne39 on 2012-03-22
Hi, you need ndiswrapper with this device it will be best to get help in this forum for it.
[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)
Thanks

---

### Post by Frogs Hair on 2012-03-22
I know one person who has used this with success. [http://www.dban.org/](http://www.dban.org/)

---

