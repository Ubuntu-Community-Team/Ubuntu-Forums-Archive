---
title: "ndiswrapper: hardware present, network settings: nothing"
date: 2006-05-30
forum: General Help
---

### Post by 1002285 on 2006-05-30
I tried to install my wifi card - Canyon CN-WF518, with ndiswrapper and windows driver.
Ndiswrapper's graphic interface "installed windows drovers" now says:
zd1211u
Hardware present: Yes
but it does not show up in my network settings - there is still only eth0 and modem available
What does it mean, and can I do anything about it?

---

### Post by Nonno Bassotto on 2006-05-30
Be sure that the module ndiswrapper is loaded. To do so type
```

lsmod | grep ndis

```
and look if the word ndiswrapper appears. If not try
```

sudo modprobe ndiswrapper

```
to load the driver. Now your card should appear in the network dialog. If not, post here the result of
```

lsmod

```

---

### Post by 1002285 on 2006-05-30
I guess nothing appeared after sudo modprobe ndiswrapper
Here is the result of lsmod:
Module                  Size  Used by
ndiswrapper           114376  0
af_packet              20232  2
8139cp                 18432  0
8139too                23552  0
mii                     5248  2 8139cp,8139too
isofs                  32824  1
udf                    75524  0
ipv6                  217408  8
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
pcmcia                 24584  4
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
floppy                 52692  0
zd1211                182020  0
pcspkr                  3652  0
rtc                    11832  0
snd_nm256              67680  20
snd_ac97_codec         72188  1 snd_nm256
snd_pcm_oss            46368  0
snd_mixer_oss          16128  20 snd_pcm_oss
snd_pcm                78344  3 snd_nm256,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10120  1 snd_pcm
i2c_piix4               8336  0
i2c_core               19728  2 i2c_acpi_ec,i2c_piix4
yenta_socket           22540  3
rsrc_nonstatic         12032  1 yenta_socket
pcmcia_core            44932  3 pcmcia,yenta_socket,rsrc_nonstatic
pci_hotplug            24628  0
intel_agp              21276  1
agpgart                32328  1 intel_agp
nls_cp437               5888  1
vfat                   12288  1
fat                    46492  1 vfat
nls_utf8                2176  3
ntfs                   92016  1
dm_mod                 50364  1
joydev                  9280  0
snd_seq_dummy           3844  0
tsdev                   7616  0
snd_seq_oss            29440  0
snd_seq_midi            8608  0
snd_rawmidi            22816  1 snd_seq_midi
snd_seq_midi_event      6656  2 snd_seq_oss,snd_seq_midi
evdev                   9088  1
snd_seq                44688  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              21764  2 snd_pcm,snd_seq
snd_seq_device          8204  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    48644  13 snd_nm256,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9184  20 snd
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
uhci_hcd               28048  0
usbcore               104316  4 ndiswrapper,zd1211,uhci_hcd
ide_cd                 36996  1
cdrom                  33952  1 ide_cd
ide_disk               16128  5
ide_generic             1664  0
piix                    9476  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,piix
unix                   24624  726
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon

---

### Post by Nonno Bassotto on 2006-05-31
I have to say I'm not an expert. I may also mention that tomorrow Dapper (Ubuntu next release) will be stable, so you could upgrade the distro. Maybe your problem will already be fixed in Dapper.
If you don't want to upgrade, then read on.

It seems you have loaded both ndiswrapper and linux native driver for you card (zd1211). This may give you some conflicts, so if you wish to use ndiswrapper and experience some problems, you could try to remove the other driver by
```

sudo modprobe -r zd1211

```
Anyway, this shouldn't prevent you from seeing your hardware in the Network dialog. ](*,) 
If this doesn't work (and I guess it won't), you can reload it again by
```

sudo modprobe zd1211

```
Have a look if your hardware is recognized at all. The command
```

lsusb

```
will present you a list of the devices attached to usb ports. Is your card listed there?
Another thing you can check:
```

ndiswrapper -l

```
lists the drivers loaded with ndiswrapper, but I think it should give you the same answer of the graphical dialog.
Post here the results of the commands I mentioned. If everything seems alright but still you can't see your card... :( I'm out of ideas. As I said I'm a linux noob, so I hope someone more experienced will give you help.
Anyway, consider first the idea of using Dapper.

---

### Post by 1002285 on 2006-05-31
ok, here it is.
lsusb:
Bus 001 Device 002: ID 0ace:1211
Bus 001 Device 001: ID 0000:0000
ndiswrapper -l
Installed ndis drivers:
zd1211u driver present, hardware present

But it does not show up in the choice of network options. There's still only ethernet and modem.
So does it mean you are out of ideas?

The thing with Dapper is that I have tried it and in Dapper even my ethernet card was lost, so I did not have any network at all and I came back to Breezy.

But I was surprised that you said you thought I had native linux driver loaded. I had tried with a driver file, but it alwas gave some errors and I did not think it was loaded. Then I tried with ndiswrapper and Windows driver.

---

### Post by 1002285 on 2006-05-31
And when I try to install the linux native driver again:
sudo dpkg -i CN-WF518_Mac_drv
dpkg-deb: `CN-WF518_Mac_drv' is not a debian format archive
dpkg: error processing CN-WF518_Mac_drv (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 CN-WF518_Mac_drv

A funny thing is that Canyon has removed the page where I got the driver file from.
I had contacted them via web support to ask what to do with the driver - they answered "install it" - and when I contacted them again, I got no more response. And now the page is gone.
I did not even understand, why the file did not have an extension: CN-WF518_Mac_drv
So I have to say i really don't no much about Linux.

---

### Post by Nonno Bassotto on 2006-05-31
I said you have the driver installed because in the lsmod result there is the line
```

usbcore 104316 4 ndiswrapper,zd1211,uhci_hcd

```
and according to [http://zd1211.ath.cx/](http://zd1211.ath.cx/) zd1211 is the linux driver for various wifi cards, among which there is yours. Anyway it seems that even lsusb doesn't list correctly your wifi card. I will search a bit to understand better what's happening, but I don't have ideas anymore, I'm a newbie too.
Try posting again your question (sometimes people that wish to help search unanswered post, so may not notice your request). Hope you find how to connect.
When tomorrow the definitive dapper comes out, try the live cd to see if it works for you. If the ethernet works, you can even install ndiswrapper and test immediately if your problem has gone (don't worry, nothing will be really installed, it will just stay in the memory until you shutdown the computer).

---

### Post by Nonno Bassotto on 2006-05-31
Actually there is one last thing you could try, that is, configuring your wifi using the terminal, at least until you get the graphic tool to work. But I have to warn you that I don't think anything will change.
Anyway, try typing
```

iwconfig

```
and cross your fingers. If you don't see an entry about your wifi card, then hope someone else will try to help you. :( 
But if it shows an entry, then you should be able to configure it using the iwconfig command itself, and then activate it with
```

sudo ifup wlan0

```
(change wlan0 to the identifier of your card in iwconfig). I won't enter into the details because they are described in
[https://wiki.ubuntu.com/WiFiHowto](https://wiki.ubuntu.com/WiFiHowto)
so you can read there.

---

### Post by 1002285 on 2006-05-31
Thank you very much for trying to help.
iwconfig did not show the card.

I'm beginning to think more and more that this has sth to do with the "starting hotplug subsystem hang" that was my first big problem with ubuntu. It seems to have been quite a common problem for ubuntu users with laptops and people have not found a good solution - they have either had to switch off sound or sth else. I guess it is a bug that has not been fixed in 5.10.

For example, the light on the USB Wifi card is lit during the boot until the system is finally loaded - then it's gone. And, while the system has somehow "got used to" booting without hanging at the "starting hotplug subsystem", with the ethernet card in, it did hang when I tried booting with the usb card inserted.

So I'll try to put up another post that is hopefully more informative from my own part.

About dapper - I think I can't use an install CD, because I don't have a DVD reader, and dapper does not come on a CD? And when I upgrade via network, I can't come back anymore without a clean install I guess. Or can I try it somehow?

---

### Post by Nonno Bassotto on 2006-06-01
When Dapper comes out, there will be both an install and a live CD. I suggest you try the live CD, so you can see what is working and what is not. The DVD is optional (I think it will only contain Ubuntu, Kubuntu and Edubuntu all on one media, but I'm not sure of this).

---

### Post by 1002285 on 2006-06-01
OK, I'll burn that CD and see what I can do.
Thanks.

---

### Post by 1002285 on 2006-06-01
I burned a release candidate of 6.06, but as I have read, it shouldn have been a very different version.
It hanged at the stage "loading hardware drivers". I tried to boot from it both with the PCMCIA ethernet card connected and USB wifi card disconnected and vice versa, and with both of them disconnected - the result was the same: hanged in "loading hardware drivers".
I guess I'll make a new post with the same text, too.

---

