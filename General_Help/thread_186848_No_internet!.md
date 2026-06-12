---
title: "No internet!"
date: 2006-06-02
forum: General Help
---

### Post by mattm591 on 2006-06-02
**[COLOR="Red"]EDIT: SOLUTION![/COLOR]**

Thanks to Belarios for this!

> 
If you're using the 2.6.15-23-386 stock kernel, you can try this updated forcedeth.ko to see if it solves your problem. (forcedeth is an open source driver for nforce ethernet.)

I have an Asrock K8NF4G-SATAII board that uses an nForce 410 (MCP51) chipset. The version of forcedeth in Breezy didn't support the MCP51 chipset, so I went to Dapper. The 0.48 version in Dapper does support the MCP51 (and MCP55), but has a bug if you dual boot to Windows. Windows leaves the card in a state that forcedeth can't access and only disconnecting your power supply for 15 seconds will reset it. This bug was apparently fixed in version 0.53 of forcedeth.

I'm a linux newb, so I spent several hours figuring out how to get the 2.6.16 kernel from kernel.org which has version 0.49 of forcedeth, and then applying the 2.6.17 patches which patch it to 0.54. Then compiling the 0.54 version to a binary for Ubuntu Dapper 2.6.15-23-386. It was a daunting task for me, though probably an 8 minute operation for most of the people on this board.

So, if you're using the stock 2.6.15-23-386, you can try replacing the forcedeth.ko file at /lib/modules/2.6.15-23-386/kernel/drivers/net/forcedeth.ko with this one: [http://brianmercer.com/forcedeth.ko](http://brianmercer.com/forcedeth.ko) which is patched to version 0.54. (Change the name of the old one to keep as a backup, of course)

If you're not using the i386 version of the kernel, you'd have to compile the driver yourself. The 0.54 source is at [http://brianmercer.com/forcedeth.c](http://brianmercer.com/forcedeth.c)


Hi,
I have an nForce 590 SLI Series motherboard and am trying to use it's built in ethernet to connect to the internet with Dapper. I have tried both ports but neither will work and I don't know wht to do. This is a new computer and I never had any problems getting my ethernet connection to work on my old one so I'm not sure how to fix this.
Can anyone give me a hand :)
Thanks,
Matt

---

### Post by thasheep on 2006-06-02
If it's new, it's possible your ethernet card is not (yet) supported. In any case, print the output of 'lspci'. This will show what cards you have - the first step to determining what driver is needed.

---

### Post by mattm591 on 2006-06-02
Output of lspci is as follows:

> 
0000:00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
0000:00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
0000:00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
0000:00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
0000:00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
0000:00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
0000:00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
0000:00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
0000:00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
0000:00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
0000:00:08.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
0000:00:09.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
0000:00:09.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
0000:00:09.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
0000:00:0a.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
0000:00:0a.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
0000:00:0c.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
0000:00:0d.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
0000:00:0d.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
0000:00:0d.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
0000:00:0e.0 PCI bridge: nVidia Corporation: Unknown device 0370 (rev a2)
0000:00:0e.1 0403: nVidia Corporation: Unknown device 0371 (rev a2)
0000:00:10.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
0000:00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
0000:00:12.0 PCI bridge: nVidia Corporation: Unknown device 0376 (rev a2)
0000:00:14.0 PCI bridge: nVidia Corporation: Unknown device 0374 (rev a2)
0000:00:16.0 PCI bridge: nVidia Corporation: Unknown device 0375 (rev a2)
0000:00:17.0 PCI bridge: nVidia Corporation: Unknown device 0377 (rev a2)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:02:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0290 (rev a1)
0000:03:07.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
0000:03:07.1 Input device controller: Creative Labs SB Audigy MIDI/Game port (rev 04)
0000:03:07.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
0000:03:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
0000:06:00.0 Mass storage controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)


---

### Post by thasheep on 2006-06-02
As you may have guessed, your ethernet controller is```
0000:00:10.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
0000:00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
```nVidia has a funny way of supporting linux and releases drivers with restrictive licenses. I'm not entirely sure what driver you need but you could be lucky and it could be in the restricted drivers package. In synaptic package manager, enable the restricted repositories (if you haven't already), settings>repositories>ubuntu 6.06 LTS (binary) - edit and select restricted copyright. Now search for linux-restricted-modules and select linux-restricted-modules-[whatever corresponds to your kernel (386/686/k7/etc)]
Restart and cross your fingers.

---

### Post by mattm591 on 2006-06-02
Already were enabled, so that isn't it

---

### Post by nixt on 2006-06-02
I would guess that the driver isn't already there. Your motherboard is too new! Wish i had yours though :)

---

### Post by mattm591 on 2006-06-02
Hehe, it's an awesome PC, just no net :( so is there nothing I can do to connect to the internet? :'(

---

### Post by nixt on 2006-06-02
Is there anything you can pick out off the motherboard drivers CD? I can't find anything myself off google...

---

### Post by dglock on 2006-06-02
[QUOTE=mattm591]Hehe, it's an awesome PC, just no net :( so is there nothing I can do to connect to the internet? :'([/QUOTE]

  Ethernet cards are cheap, pick up a link-sys or other card to use until ubuntu catches up with the drivers.

  don

---

### Post by Fass on 2006-06-02
What does lsmod say? I believe the module for MCP55 is amd74xx and possibily forcedeth for the ethernet.

---

### Post by mattm591 on 2006-06-02
Hi,
Thanks for the replys guys.
lsmod gives the following output:
> 
Module                  Size  Used by
nls_cp437               5888  1
isofs                  37688  1
udf                    88452  0
ipv6                  265600  6
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
md_mod                 72532  0
sr_mod                 16932  0
sbp2                   24196  0
lp                     11844  0
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
pcspkr                  2180  0
snd_emu10k1_synth       7296  0
snd_emux_synth         37376  1 snd_emu10k1_synth
snd_seq_virmidi         7680  1 snd_emux_synth
snd_seq_midi_emul       7168  1 snd_emux_synth
snd_seq_dummy           3844  0
snd_seq_oss            33536  0
snd_seq_midi            9376  0
snd_seq_midi_event      7552  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
r8187                  41860  0
snd_seq                51984  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ieee80211_rtl          83592  1 r8187
floppy                 62148  0
rtc                    13492  0
psmouse                36228  0
snd_emu10k1           117156  2 snd_emu10k1_synth
snd_rawmidi            25504  3 snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_ac97_codec         92704  1 snd_emu10k1
snd_ac97_bus            2304  1 snd_ac97_codec
snd_seq_device          8716  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
emu10k1_gp              3840  0
gameport               15496  2 emu10k1_gp
snd_util_mem            4608  2 snd_emux_synth,snd_emu10k1
sata_sil24             11524  0
serio_raw               7300  0
snd_hwdep               9376  2 snd_emux_synth,snd_emu10k1
snd_hda_intel          18964  1
snd_hda_codec         142640  1 snd_hda_intel
af_packet              22920  2
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  6 snd_emu10k1,snd_ac97_codec,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25220  3 snd_seq,snd_emu10k1,snd_pcm
snd                    55268  18 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_ac97_codec,snd_seq_device,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  3 snd_emu10k1,snd_hda_intel,snd_pcm
nvidia               4550772  0
agpgart                34888  1 nvidia
i2c_core               21904  2 i2c_acpi_ec,nvidia
sg                     37920  0
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
tsdev                   8000  0
evdev                   9856  3
ext3                  135688  2
jbd                    58772  1 ext3
dm_mod                 58936  4
usbhid                 38368  0
ide_generic             1536  0
ehci_hcd               32008  0
ohci1394               35124  0
ieee1394              299832  2 sbp2,ohci1394
ohci_hcd               21892  0
usbcore               129668  5 r8187,usbhid,ehci_hcd,ohci_hcd
forcedeth              23428  0
ide_cd                 33028  1
cdrom                  38560  2 sr_mod,ide_cd
generic                 5124  0
amd74xx                15132  0 [permanent]
sd_mod                 19984  4
sata_nv                 9604  5
libata                 78992  2 sata_sil24,sata_nv
scsi_mod              139496  6 sr_mod,sbp2,sata_sil24,sg,sd_mod,libata
thermal                13576  0
processor              23360  1 thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit


---

### Post by mattm591 on 2006-06-02
Ooops, didn't see it'd gone to a second page. Sorry for double post.

---

### Post by Fass on 2006-06-02
What does dmesg say about forcedeth?

---

### Post by mattm591 on 2006-06-02
I found these references to forcedeth

> 
[4294674.676000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.48.

[4294675.189000] eth0: forcedeth.c: subsystem: 010de:cb84 bound to 0000:00:10.0


---

### Post by Belarios on 2006-06-02
If you're using the 2.6.15-23-386 stock kernel, you can try this updated forcedeth.ko to see if it solves your problem. (forcedeth is an open source driver for nforce ethernet.)

I have an Asrock K8NF4G-SATAII board that uses an nForce 410 (MCP51) chipset.  The version of forcedeth in Breezy didn't support the MCP51 chipset, so I went to Dapper.  The 0.48 version in Dapper does support the MCP51 (and MCP55), but has a bug if you dual boot to Windows.  Windows leaves the card in a state that forcedeth can't access and only disconnecting your power supply for 15 seconds will reset it.  This bug was apparently fixed in version 0.53 of forcedeth.

I'm a linux newb, so I spent several hours figuring out how to get the 2.6.16 kernel from kernel.org which has version 0.49 of forcedeth, and then applying the 2.6.17 patches which patch it to 0.54.  Then compiling the 0.54 version to a binary for Ubuntu Dapper 2.6.15-23-386.  It was a daunting task for me, though probably an 8  minute operation for most of the people on this board.

So, if you're using the stock 2.6.15-23-386, you can try replacing the forcedeth.ko file at /lib/modules/2.6.15-23-386/kernel/drivers/net/forcedeth.ko with this one: [http://brianmercer.com/forcedeth.ko](http://brianmercer.com/forcedeth.ko) which is patched to version 0.54.  (Change the name of the old one to keep as a backup, of course)

If you're not using the i386 version of the kernel, you'd have to compile the driver yourself.  The 0.54 source is at [http://brianmercer.com/forcedeth.c](http://brianmercer.com/forcedeth.c)

You could also try the nvnet driver from nvidia.  Let me know if you need more detailed instructions to try replacing the forcedeth driver as described above.

---

### Post by wuch on 2006-06-03
Thank you! After a whole day of reading forum posts and calling ifconfig, lsmod, and lspci I finally found this post. I disconnected my power supply for 15 seconds and I'm online now!

Unfortunately, I'm even more of a newb. So can you tell me what I need to do with forcedeth.c in order to create the module for a 2.6.15-23-amd64-generic kernel? Thanks.

---

### Post by mattm591 on 2006-06-03
Thanks for that Belarious, I'll give it a whril when I get back from work tonight and let you know how I got on :P

---

### Post by Belarios on 2006-06-03
Wuch, you'll need the kernel headers and the compiler and the make utility.

For the kernel headers you should be able to do: 

```
sudo apt-get install linux-headers-`uname -r`
```

(note that the "`" is the reverse single quotation mark with the tilde "~" key, generally to the left of the number one "1" key.)

And for the compiler and make utility you should be able to do the following which gets the "make" package and the "gcc" package which grabs the right version of the gcc compiler:

```
sudo apt-get install build-essential
```

Now, create a directory and put the forcedeth.c file in there.  Create a new file in that directory using a text editor and name the file "Makefile". Add the following one line of text to the new Makefile:

```
obj-m := forcedeth.o
```

Then go to that directory and do:

```
sudo make -C /usr/src/linux-headers-`uname -r` SUBDIRS=$PWD modules
```

That will create the forcedeth.ko kernel module.  Let us know if there's any difference under the 64bit version, or if I left anything out.

---

### Post by Belarios on 2006-06-03
I'm assuming that if and when a serious bug or security flaw is discovered in the kernel that the ubuntu maintainers will upload a new kernel and we'll have to go thru this again.

---

### Post by mattm591 on 2006-06-03
Thanks for this, worked a treat and nets working fine! Saved me hours of headaches :P

---

### Post by Snatch on 2006-06-03
how can i copy forcedeth.ko to /bin/.../net/    ?

in live cd I can connect to the internet...

---

### Post by mattm591 on 2006-06-04
To copy use these commands in termainl

cd the_directory_new_forcedeth.ko_is_in

sudo cp forcedeth.ko /lib/modules/2.6.15-23-386/kernel/drivers/net/

That should work fine.

---

### Post by Snatch on 2006-06-04
thank you,
but in my case don´t work... I continue without internet :(

---

### Post by mattm591 on 2006-06-05
Have you tried turning the power off for 15 seconds then booting straight into ubuntu. If that doesn't work the chances are your problem isn't with forcedeth.

---

### Post by Tombius on 2006-06-05
HI there!, seems like Ubuntu doesnt want to work with me, First of all i couldnt use version 5.04 because it didnt recognize my sata hdd, next couldnt use 5.10 because ok now recognized Sata Hdd but now my video card was not supported at the time. Its an integrated GPU GeForce6100 /nForce 430, then 4 days ago saw the Dapper drake release 6.06 tought i finally could be able to work with ubuntu and then thisd one supported Sata HDD, suported my GPU, but when i was going to surf the net, started to cry, what is a life without internet connection?. I am writting this in XP session, and seems that the real deal (or should i say pain) is that XP disables the network hardware. I know there is A LOT of people suffering with newest motherboards and specially with integrated GPU and Ethernet devices, and besides have to share the HDD with an XP partition. 

I am going to try the shut down and unplug the powersource method, should it work to me, at least all the Nvidia graphics, Sata Disks, Partition Shared, Internet disabled users will finally find in dapper drake the chance to use Ubuntu without reprogramming kernels and making all sorts of tricks voodoo magic and arcane spells to make it fully functional. Attention all the 

GYGABYTE

GA-K8N51GMF-9 USERS 
(and i can take the risk to say that similar motherboard users may find this useful)

SPECS TO TRY:

Nvidia GeForce6100/nForce 430
Socket 939/Micro Atx/ 
DDR400 Dual Channel-512Mb Kingston
Sata HDD 120 Gb in XP partition - 40 Gb in Ubuntu Dapper drake
AMD Athlon 64 3000+

See you back in Drake if it works.

---

### Post by Tombius on 2006-06-05
Hell yes!!! This really works. I am on Dapper Drake now, altough i dont know how long this is going to be effective, i only know one thing -life has come to me again-.

SIMILAR USERS MUST TRY THIS BEFORE ANY FANCY SOLUTIONS.
Got to surf see ya.

---

### Post by Snatch on 2006-06-05
[QUOTE=mattm591]Have you tried turning the power off for 15 seconds then booting straight into ubuntu. If that doesn't work the chances are your problem isn't with forcedeth.[/QUOTE]

yes I tried but not work.
But one strange thing is running ubuntu live cd i have internet... after install I don't have internet

appears 127.0...
and eth0 but without IP, I use a router(linksys wrt54g) with DHCP.
sorry for my english ](*,)  im portuguese

---

### Post by mattm591 on 2006-06-06
My net didn't work properly straight away. I also have DHCP with a router although mines Belkin,. To get my net working I had to put my routers IP address (in my case 192.168.2.1) into the DNS servers box (find it in the Networking panel, go to the DNS tab then theres a DNS servers list)

---

### Post by Belarios on 2006-06-06
OK Snatch, lets start from the beginning.  You haven't said what brand and model of ethernet card (or onboard) that you're using.  So do a [list pci hardware]:
```
lspci
```
For example, on my system, it returns a whole bunch of lines listing memory controllers and USB controllers and also these two lines:
```
...
0000:00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
...
0000:04:08.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)
...
```
OK, so now we know I have the NVIDIA MCP51 onboard controller and also a PCI card in there that's based on the Davicom 21x4x.
Now lets see if I have drivers loaded for those.  I know that the driver for my NVIDIA card is called forcedeth and for the Davicom card there's been alot of advice on this board about how it uses tulip by default, but you need to change that to the dmfe driver.  The drivers are loaded as kernel modules so lets [list modules]:
```
lsmod
```
Among all of the modules loaded, I can see
```
...
dmfe                   21532  0
tulip                  51872  0
...
forcedeth              30476  0
...
```
OK! I have all three of those loaded.  (although in the howtos on this forum they recommend disabling tulip to make sure that the card uses dmfe).  Lets see how the hardware is assigned by checking the system message buffer.  Since that'll be very long, we're going to use grep to filter only the responses that contain the letters "eth".
```
dmesg | grep eth
```
For me, that produces the following output:
```
[4294674.682000] Driver 'sd' needs updating - please use bus_type methods
[4294676.067000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.54.
[4294676.067000] forcedeth: using HIGHDMA
[4294676.580000] eth0: forcedeth.c: subsystem: 01849:0269 bound to 0000:00:14.0
[4294684.182000] eth1: Davicom DM9102/DM9102A rev 49 at 0001c800, 00:08:A1:84:3E:0A, IRQ 50.
[4294699.363000] eth0: no IPv6 routers present

```
So that shows the nvidia card using forcedeth and assigned eth0 and the Davicon card on eth1.  It also happens to show the forcedeth driver on version 0.54 because I patched it.  I could check the dmfe driver by doing *dmesg | grep dmfe* and check the version of that one too.

Well that looks ok, now lets see how the interfaces are configured with:
```
ifconfig
```
For me this shows:
```

eth0      Link encap:Ethernet  HWaddr 00:13:8F:49:27:59
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:8fff:fe49:2759/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3961603 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4331260 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:339214659 (323.5 MiB)  TX bytes:1768470410 (1.6 GiB)
          Interrupt:217 Base address:0xe000

eth1      Link encap:Ethernet  HWaddr 00:08:A1:84:3E:0A
          inet6 addr: fe80::208:a1ff:fe84:3e0a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:50 Base address:0xc800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:67 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4214 (4.1 KiB)  TX bytes:4214 (4.1 KiB)

```
That's three interfaces.  One is the local loopback device which is just a handy virtual interface to the local machine.  We can see from the others that eth0 (which we know is the nvidia card) has been assigned an ip address: 192.168.0.102 while eth1 (Davicom) has no ip address.  In fact, I'm not using the Davicom device at all, so I can disable it, also using the interface configuration utility by doing:
```
sudo ifconfig eth1 down
```
I need the "sudo" in there, because I need root permission to activate and disable hardware, and that's also why it asks for a password.  I could activate the interface again by replacing the down with "up".  Now that we've done the background work, and confirmed our brand and model and made sure we're using the correct driver, we seem to be at the point that you're at.  You have an activated interface, but no ip address.  You said that your router uses DHCP.  (DHCP is a system for handing out ip addresses where one device is the DHCP server and the other devices make a polite client request for an address)  Your router/gateway is the DHCP server, and your computer is going to use a DHCP client application to ask for an ip address, so do the command:
```
sudo dhclient eth0
```
On my system, that produces the following response:
```
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP
Listening on LPF/eth0/00:13:8f:49:27:59
Sending on   LPF/eth0/00:13:8f:49:27:59
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.102 -- renewal in 3484585 seconds.

```
Which says that my ethernet card (which is identified with it's unique hardware MAC address of 00:13:8f:49:27:59) is sending a DHCP request out on the "broadcast" address of 255.255.255.255 and then listening for a reply.  The router, which listens for such requests, is sending back a DHCP acknowledgement from ip address 192.168.0.1 (which is the router's address).  The result is that my computer has been granted the temporary use of ip address 192.168.0.102 and that this "lease" of the ip address will expire many seconds from now.

Success for me!  Now this is the manual way of doing all this.  You shouldn't need to do all that manually.  It should all be done automatically at startup.  But we're doing it manually to see at what point the system is breaking down.  If you can do it all manually, then we'll move on and see if it's the automatic startup process that isn't working correctly.

So now, please tell us, what brand and model of ethernet card you're using, which driver you're using and is it loaded, is the interface being brought up, and are you getting any response to your DHCP request?

---

### Post by Belarios on 2006-06-06
A couple notes about my solution of replacing the version 0.48 of forcedeth with the newer 0.54 version.  

This only seems to matter for motherboards using the newer nforce 410 and 430 chips.  Forcedeth worked fine with nforce and nforce2 and nforce3 and nforce4.  You couldn't even use the nforce 410 or 430 with breezy because breezy had version 0.32 of forcedeth which didn't support them yet.  You can see that the support for nforce 410/430 was added in with revisions 0.33 and 0.35 (MCP51 is also called nforce410 and MCP55 is also known as nforce430): 

```

* Changelog:
 * 	0.01: 05 Oct 2003: First release that compiles without warnings.
 * 	0.02: 05 Oct 2003: Fix bug for nv_drain_tx: do not try to free NULL skbs.
 * 			   Check all PCI BARs for the register window.
 * 			   udelay added to mii_rw.
 * 	0.03: 06 Oct 2003: Initialize dev->irq.
 * 	0.04: 07 Oct 2003: Initialize np->lock, reduce handled irqs, add printks.
 * 	0.05: 09 Oct 2003: printk removed again, irq status print tx_timeout.
 * 	0.06: 10 Oct 2003: MAC Address read updated, pff flag generation updated,
 * 			   irq mask updated
 * 	0.07: 14 Oct 2003: Further irq mask updates.
 * 	0.08: 20 Oct 2003: rx_desc.Length initialization added, nv_alloc_rx refill
 * 			   added into irq handler, NULL check for drain_ring.
 * 	0.09: 20 Oct 2003: Basic link speed irq implementation. Only handle the
 * 			   requested interrupt sources.
 * 	0.10: 20 Oct 2003: First cleanup for release.
 * 	0.11: 21 Oct 2003: hexdump for tx added, rx buffer sizes increased.
 * 			   MAC Address init fix, set_multicast cleanup.
 * 	0.12: 23 Oct 2003: Cleanups for release.
 * 	0.13: 25 Oct 2003: Limit for concurrent tx packets increased to 10.
 * 			   Set link speed correctly. start rx before starting
 * 			   tx (nv_start_rx sets the link speed).
 * 	0.14: 25 Oct 2003: Nic dependant irq mask.
 * 	0.15: 08 Nov 2003: fix smp deadlock with set_multicast_list during
 * 			   open.
 * 	0.16: 15 Nov 2003: include file cleanup for ppc64, rx buffer size
 * 			   increased to 1628 bytes.
 * 	0.17: 16 Nov 2003: undo rx buffer size increase. Substract 1 from
 * 			   the tx length.
 * 	0.18: 17 Nov 2003: fix oops due to late initialization of dev_stats
 * 	0.19: 29 Nov 2003: Handle RxNoBuf, detect & handle invalid mac
 * 			   addresses, really stop rx if already running
 * 			   in nv_start_rx, clean up a bit.
 * 	0.20: 07 Dec 2003: alloc fixes
 * 	0.21: 12 Jan 2004: additional alloc fix, nic polling fix.
 *	0.22: 19 Jan 2004: reprogram timer to a sane rate, avoid lockup
 *			   on close.
 *	0.23: 26 Jan 2004: various small cleanups
 *	0.24: 27 Feb 2004: make driver even less anonymous in backtraces
 *	0.25: 09 Mar 2004: wol support
 *	0.26: 03 Jun 2004: netdriver specific annotation, sparse-related fixes
 *	0.27: 19 Jun 2004: Gigabit support, new descriptor rings,
 *			   added CK804/MCP04 device IDs, code fixes
 *			   for registers, link status and other minor fixes.
 *	0.28: 21 Jun 2004: Big cleanup, making driver mostly endian safe
 *	0.29: 31 Aug 2004: Add backup timer for link change notification.
 *	0.30: 25 Sep 2004: rx checksum support for nf 250 Gb. Add rx reset
 *			   into nv_close, otherwise reenabling for wol can
 *			   cause DMA to kfree'd memory.
 *	0.31: 14 Nov 2004: ethtool support for getting/setting link
 *			   capabilities.
 *	0.32: 16 Apr 2005: RX_ERROR4 handling added.
 *	0.33: 16 May 2005: Support for MCP51 added.
 *	0.34: 18 Jun 2005: Add DEV_NEED_LINKTIMER to all nForce nics.
 *	0.35: 26 Jun 2005: Support for MCP55 added.
 *	0.36: 28 Jun 2005: Add jumbo frame support.
 *	0.37: 10 Jul 2005: Additional ethtool support, cleanup of pci id list
 *	0.38: 16 Jul 2005: tx irq rewrite: Use global flags instead of
 *			   per-packet flags.
 *	0.39: 18 Jul 2005: Add 64bit descriptor support.
 *	0.40: 19 Jul 2005: Add support for mac address change.
 *	0.41: 30 Jul 2005: Write back original MAC in nv_close instead
 *			   of nv_remove
 *	0.42: 06 Aug 2005: Fix lack of link speed initialization
 *			   in the second (and later) nv_open call
 *	0.43: 10 Aug 2005: Add support for tx checksum.
 *	0.44: 20 Aug 2005: Add support for scatter gather and segmentation.
 *	0.45: 18 Sep 2005: Remove nv_stop/start_rx from every link check
 *	0.46: 20 Oct 2005: Add irq optimization modes.
 *	0.47: 26 Oct 2005: Add phyaddr 0 in phy scan.
 *	0.48: 24 Dec 2005: Disable TSO, bugfix for pci_map_single
 *	0.49: 10 Dec 2005: Fix tso for large buffers.
 *	0.50: 20 Jan 2006: Add 8021pq tagging support.
 *	0.51: 20 Jan 2006: Add 64bit consistent memory allocation for rings.
 *	0.52: 20 Jan 2006: Add MSI/MSIX support.
 *	0.53: 19 Mar 2006: Fix init from low power mode and add hw reset.
 *	0.54: 21 Mar 2006: Fix spin locks for multi irqs and cleanup.

```

Pulling the cord out of the back of your computer for 15 seconds is a good way to test to see if this indeed is your problem.  Remember that simply turning off your computer from the front will not work because the power supply still supplies a small amount of power to keep the computer in a convenient ready state.  If your power supply has a switch on the back, that should work the same as pulling the cord out, but not all computer power supplies have that switch.

---

### Post by Snatch on 2006-06-06
Belarios, thank you!

while I followed the steps, I checked ipconfig and my interface are not configured! 

```
eth0      Link encap:Ethernet  HWaddr 00:11:D8:5E:C9:97
          inet6 _**addr: fe80::211:d8ff:fe5e:c997/64**_ Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5515 (5.3 KiB)  TX bytes:468 (468.0 b)
          Interrupt:217 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)
```

so i maded this:

[[IMG]http://img119.imageshack.us/img119/1160/screenshotinterfaceproperties6.png[/IMG]](http://imageshack.us)

```
eth0      Link encap:Ethernet  HWaddr 00:11:D8:5E:C9:97
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:d8ff:fe5e:c997/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2586 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2422 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1827950 (1.7 MiB)  TX bytes:425477 (415.5 KiB)
          Interrupt:217 Base address:0xe000

```

and now I'm in ubuntu writing this.

Muito Obrigado :D  -> translation   [thanks a lot] :wink:

---

### Post by Belarios on 2006-06-06
Great work.  Assigning a static ip address (i.e. manually entering an ip address that you choose, instead of having the DHCP system assign you one dynamically when you boot the machine) is a good solution!

---

### Post by ajbucci on 2006-06-07
Belarious, i followed your instructions for making the foredeth.ko file for AMD64 but i got this error:

```
sudo make -C /usr/src/linux-headers-2.6.15-23 SUBDIRS=$PWD modules
make: Entering directory `/usr/src/linux-headers-2.6.15-23'

  WARNING: Symbol version dump /usr/src/linux-headers-2.6.15-23/Module.symvers
           is missing; modules will have no dependencies and modversions.

make[1]: *** No rule to make target `/home/anthony/forcedeth/forcedeth.c', needed by `/home/anthony/forcedeth/forcedeth.o'.  Stop.
make: *** [_module_/home/anthony/forcedeth] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.15-23'
```

I'm pretty much completely new to linux.

---

### Post by Belarios on 2006-06-07
OK, I think I see my mistake.  To make sure that you have the proper headers for your version of the kernel do
```

sudo apt-get install linux-headers-`uname -r`

```
(note that the "`" is the reverse single quotation mark with the tilde "~" key, generally to the left of the number one "1" key.)

And then do
```

sudo make -C /usr/src/linux-headers-`uname -r` SUBDIRS=$PWD modules

```

Thanks for the catch. I changed it in the earlier post also.

---

### Post by Exussum on 2006-06-07
```
scott@Scott:~/forcedeth$ sudo apt-get install linux-headers-`uname -r`
Password:
Reading package lists... Done
Building dependency tree... Done
linux-headers-2.6.15-23-amd64-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up samba (3.0.22-1ubuntu3) ...
update-rc.d: warning: /etc/rc2.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
update-rc.d: warning: /etc/rc3.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 102
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

is the error message i get for the first one

```
scott@Scott:~/forcedeth$ sudo make -C /usr/src/linux-headers-`uname -r` SUBDIRS=$PWD modules
make: Entering directory `/usr/src/linux-headers-2.6.15-23-amd64-generic'
scripts/Makefile.build:15: /home/scott/forcedeth/Makefile: No such file or directory
make[1]: *** No rule to make target `/home/scott/forcedeth/Makefile'.  Stop.
make: *** [_module_/home/scott/forcedeth] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.15-23-amd64-generic'

```

and the error i get for the second

ajbucci, i got the same error message as you, make sure the make file is Makefile (with a capital M)

Thats fixed mine, ill host the 64 bit version on my site (unless there is somewhere else you want it)

---

### Post by Belarios on 2006-06-07
The first error has nothing to do with the module compile.  It looks like the samba package did not correctly create the init scripts that start and stop samba when the computer boots and shutsdown.  I recommend trying:
```

sudo apt-get purge samba

```
and then
```

sudo apt-get install samba

```
and it might correct itself.  

For the second problem, are you sure that you copied the forcedeth.c file into that new directory with the Makefile?  I can reproduce your error by having just the Makefile in there.  Make sure you copied the forcedeth.c file in there too.

There may need to be an additional setting somewhere for AMD64.  I can't confirm that because I'm on a 386 kernel.  I can't find anything with some quick research.  Maybe post the problem in detail in the 64 bit forum and someone will have some advice.

---

### Post by Exussum on 2006-06-07
i fixed it now - my Make file was called "makefile" 

ive attached the 64 bit kernal for use / comparision

---

### Post by vyrus on 2006-06-11
Thanks for the solution! It took me, a linux newb, the whole week. All needed is 15 seconds of power break. :-k

---

### Post by TheK on 2006-06-15
great to hear, it's fixed. But bug don't go away, if nobody reports them, so the problem will stay with the new 2.6.15-25 image.


I did that for you: [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/49870](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/49870)

---

### Post by theguyotc on 2006-06-15
[QUOTE=Belarios]So, if you're using the stock 2.6.15-23-386, you can try replacing the forcedeth.ko file at /lib/modules/2.6.15-23-386/kernel/drivers/net/forcedeth.ko with this one: [http://brianmercer.com/forcedeth.ko](http://brianmercer.com/forcedeth.ko) which is patched to version 0.54.  (Change the name of the old one to keep as a backup, of course)
[/QUOTE]

Tried this, and it works when I manually "modprobe forcedeth" once it has booted. Unfortunately, on booting it seems to somehow still use the old version, despite the fact it is no longer in /lib/modules/2.6.15-23-386/kernel/drivers/net/.  Running "dmesg | grep forcedeth" shows it is still version 0.48.

Anyone have any ideas why it is loading a file that no longer exists?

*****UPDATE*****

Found the solution. After copying the file, you have to run:
```
sudo dpkg-reconfigure linux-image-`uname -r`
```
And reboot.

---

### Post by ximian on 2006-06-19
I have an Emachines T3418 and still have no internet in Ubuntu 6.06 ,i have tried all this including the static IP and still have to power down in order to get a viable internet connection.Any help would be much appreciated.



Fixed it by buying a new network card,and opted not to use the onboard network,works now,thanks for help.....

---

### Post by wyscript on 2006-07-04
New guy to linux here.

Tried the solution that Belarios supplied, but am getting stuck halfway through. I copied and pasted the forcedeth.c text provided at the link posted by Belarios into a new file, named forcedeth.c in gedit, saved it and exited. Made sure to sudo apt-get install build-essential, then moved to the directory where forcedeth.c is located and typed:

sudo make forcedeth

There were multiple errors and warnings, the last few lines (just a fragment of the whole) which were this:

forcedeth.c:3372: warning: (near initialization for ‘driver’)
forcedeth.c:3373: error: unknown field ‘probe’ specified in initializer
forcedeth.c:3373: warning: excess elements in struct initializer
forcedeth.c:3373: warning: (near initialization for ‘driver’)
forcedeth.c:3374: error: unknown field ‘remove’ specified in initializer
forcedeth.c:3374: warning: excess elements in struct initializer
forcedeth.c:3374: warning: (near initialization for ‘driver’)
forcedeth.c: In function ‘init_nic’:
forcedeth.c:3380: error: ‘KERN_INFO’ undeclared (first use in this function)
forcedeth.c:3380: error: syntax error before string constant
make: *** [forcedeth] Error 1

I'm assuming there is a step I am missing somewhere, as it seems other people in this thread have used the same source to compile their own versions of forcedeth.ko - Still trying to figure what I'm doing wrong, but haven't a clue yet. Any help greatly appreciated!

---

### Post by imbaczek on 2006-08-01
Belarios: thanks, mate. This saved a lot of my hair.

I've got a k8n51gmf (note that it's not the -9 variant) and the onboard interface was connected to the LAN. It worked fine for a week until one day I booted to windows and installed nForce drivers - then magically it stopped working. The forcedeth you supplied worked magically after compiling it for k7 and doing rmmod/modprobe - pings from other machines started working this very instant.

This is what I found in the syslog after pinging - what is strange that this machine recieved DHCPDISCOVERs fine and appeared to respond with correct DHCPOFFERs, but those never really left the box.

Aug  1 22:04:16 imbaczek kernel: [4301113.368000] NETDEV  WATCHDOG: eth0: transmit timed out
Aug  1 22:04:16 imbaczek kernel: [4301113.368000] eth0: Got tx_timeout. irq: 00000000
Aug  1 22:04:16 imbaczek kernel: [4301113.368000] eth0: Ring at 1e48a000: next 64 nic 0
Aug  1 22:04:16 imbaczek kernel: [4301113.368000] eth0: Dumping tx registers

After dhcp3-server restart everything worked without problems. Hopefully this state of affairs won't change :)

---

### Post by Naike on 2007-08-27
That link is dead.
I use a asus crosshair mobo, which has the nforce 590 chipset.
I upgraded to Ubuntu 7.04 and still the built-in ethernet doesnt work.
is there anything that could fix this?

---

