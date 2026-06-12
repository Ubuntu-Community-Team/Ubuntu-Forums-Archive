---
title: "Comming back to linux but need advice"
date: 2006-03-22
forum: General Help
---

### Post by Antrix on 2006-03-22
Hey all.
I have been back on windows xp for a long while due to gaming on my new'ish computer system.

Now exams are comming up after easter and the only way i'll get ANY revision done over the holidays is to get RID of counter strike source (it's evil! EVIL i tell you!). I'm quite addicted. It simply has to go.

Ubuntu will be my distro of choice. I am confident in linux as a past gentoo-user but I just haven't got the time for gentoo any more.

Right.. To the point:
My Hardware:
- ASUS a8n-e motherboard
- AMD64 s939 3200+ cpu
- 1 gig corsair RAM
- Linux-compatible WIFI card for net access (i used this in my old system, breezy auto-dected etc.)
- ATI X850XT pci express graphics
- 200gb seagate barracuda SATA drive
- Onboard sound

I seem to remember trying to boot a breezy 5.10 liveCD on this system a good while ago with no success. Now... I know Dapper Drake is comming out in April, but I want to make the switch next week. I am fairly confident with kernel recompilation & configuration etc, but it's something i would like to avoid as I simply have a lot of other things to be working on.

I know ATI support for linux isn't great but I still need "reasonable" 3D acceleration for my Java3D coursework. I don't care if the drivers run at half the speed under linux as my graphics card is decent and enough for my coursework even at half speed.

What is best? Wait for dapper in april OR install 5.10 with latest updates? Anyone with similar hardware that can offer any input?

For your reference, I'll be using the system for:

1. Programming (gcc/java + java3D/php/mysql etc etc)
2. Web browsing
3. Basic Text editing/coding
4. DVD & DivX playback (and mp3 of course)
5. NO &%)(*&£% GAMES ;)

From the top of my head i think my wifi card uses the atheros chipset (?)... Is there a 64 bit driver for this? Should I go amd64 or generic x86 with my setup & requirements?

Thank you :)

---

### Post by nanotube on 2006-03-23
well, one thing i can tell you is that i have seen quite a few people have trouble with the 64 bit version, so you might want to avoid that.

i think your hardware should have no problems, but i would try it out with a livecd again just in case, to see what's up.

now you have two options - install breezy, or do the latest dapper version, which i understand is quite stable by now (flight 5). as long as you have a week to play, try dapper first, and if that doesnt pan out, wipe and breezify. :)

---

### Post by deadgobby on 2006-03-23
yes, you may want to try the new Drapper Flight CD. However, Ubie has push back Drapper release according to the news on Distro Watch.
 Here is the news on Drapper.
The controversial decision of the Ubuntu developers to postpone the final release of Dapper Drake by six weeks has met with mixed reactions. Although the decision-making process was democratic and the reasons for the proposed delay sound, the decision has its critics. Up to this point, Ubuntu Linux was about the most trustworthy Linux distribution on the market, with the reliable 6-month release cycle as one of its stated goals. Suddenly, a big part of this trust is gone and users have every reason to question the validity of Ubuntu's other promises. Besides, six weeks sounds like a long time to reach that ever elusive goal called "polish". The delay will also put more pressure on the developers - with so much extra time, the expectations will rise considerably. But let's not judge the product too early. If the extra six weeks turn Dapper Drake into the most amazing Linux distribution ever built, then be it.
 
 It is the news that SuSe has push back their new release back 6 weeks too. These guys are neck to neck and this is going to be very intresting. Cause both are fighting for #1 Linux distro.
Get get the ISO for Drapper is 
[http://www.distrowatch.cz/index.php?distribution=ubuntu&month=all&year=all](http://www.distrowatch.cz/index.php?distribution=ubuntu&month=all&year=all)
  It should have the AMD drivers but it is still Beta phase and my have some bugs, but most of the bugs may have been flushed out.
Gobby

---

### Post by deavik on 2006-03-23
[QUOTE=Antrix]
I seem to remember trying to boot a breezy 5.10 liveCD on this system a good while ago with no success. [/QUOTE]
Since you mention this I thought I should tell you what I've learnt from my own experience, ie I too tried the Breezy Live CD first and it wouldn't work (just couldn't start X even after 45 minutes. However, I took the plunge with a dual boot install and things worked out great. Now this might not be relevant (my hardware is quite different from yours I'm not going into details ...) but it still remains that a Breezy install might be better than you expect.

On the other hand, people have been pretty satisfied with Dapper from what little I've read in the Dapper forum also. :)

---

### Post by Antrix on 2006-03-23
Right guys.

I plunged into it and downloaded the Breezy 5.10 DVD release (AMD64).

The x server failed to start with "no screens found" error, so I simply fired up my fav text editor and changed the driver from "ati" to "radeon" in xorg.conf. This did the trick. So I restarted GDM and I am now posting from GNOME live session :)

I set the wireless connection up in 5 minutes using the gnome config tool (so easy) - so it's all looking good for breezy on this box.

Are the "radeon" drivers the ones i should stick with? As I said I will be doing basic Java3D and WILL need 3D rendering. Any input on this?

Also, what can I expect NOT to work using amd64? Cheers guys. Looking forward to being 100% linux again.

As you can see from lspci i'm not sure if nforce4 chipset is fully supported here (or is it?). If i update my kernel will I have better support if necessary?

If anybody are interested here is some basic system info from live session:

uname -r:
```

2.6.12-9-amd64-generic

```

lspci:
```

0000:00:00.0 Memory controller: nVidia Corporation: Unknown device 005e (rev a3)
0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 0050 (rev a3)
0000:00:01.1 SMBus: nVidia Corporation: Unknown device 0052 (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 005a (rev a2)
0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 005b (rev a3)
0000:00:04.0 Multimedia audio controller: nVidia Corporation: Unknown device 005 9 (rev a2)
0000:00:06.0 IDE interface: nVidia Corporation: Unknown device 0053 (rev f2)
0000:00:07.0 IDE interface: nVidia Corporation: Unknown device 0054 (rev f3)
0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 0055 (rev f3)
0000:00:09.0 PCI bridge: nVidia Corporation: Unknown device 005c (rev a2)
0000:00:0a.0 Bridge: nVidia Corporation: Unknown device 0057 (rev a3)
0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
0000:00:0c.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
0000:00:0d.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
0000:00:0e.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5d5 2
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 5d72
0000:05:06.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

```

lsmod:
```

wlan_wep                6912  1
ipv6                  246400  6
rfcomm                 37168  0
l2cap                  24328  5 rfcomm
bluetooth              48964  4 rfcomm,l2cap
cpufreq_userspace       5584  0
cpufreq_stats           5896  0
freq_table              5384  1 cpufreq_stats
cpufreq_powersave       2432  0
cpufreq_ondemand        7212  0
cpufreq_conservative     8236  0
video                  17416  0
tc1100_wmi              8200  0
sony_acpi               6296  0
pcc_acpi               13696  0
i2c_acpi_ec             6528  0
hotkey                 10696  0
dev_acpi               14980  0
container               5248  0
button                  7968  0
battery                10760  0
ac                      5768  0
tsdev                   8960  0
analog                 10976  0
gameport               16392  1 analog
snd_mpu401              8328  0
snd_mpu401_uart         7936  1 snd_mpu401
snd_rawmidi            27040  1 snd_mpu401_uart
snd_seq_device          9488  1 snd_rawmidi
pcspkr                  4176  0
ath_pci                80416  0
ath_rate_sample        17296  1 ath_pci
wlan                  135668  4 wlan_wep,ath_pci,ath_rate_sample
ath_hal               172144  3 ath_pci,ath_rate_sample
shpchp                 87976  0
pci_hotplug            28008  1 shpchp
snd_intel8x0           34816  1
snd_ac97_codec         87000  1 snd_intel8x0
snd_pcm_oss            51232  0
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                91020  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              24200  1 snd_pcm
snd                    55784  12 snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10912  1 snd
snd_page_alloc         11408  2 snd_intel8x0,snd_pcm
i2c_nforce2             7808  0
i2c_core               22936  2 i2c_acpi_ec,i2c_nforce2
rtc                    13448  0
psmouse                27908  0
lp                     13576  0
md                     43904  0
dm_snapshot            15672  1
dm_mod                 54904  4 dm_snapshot
loop                   16272  0
cloop                  14176  1
af_packet              22668  0
forcedeth              22144  0
nls_cp437               7424  1
isofs                  35404  1
ide_cd                 40608  1
cdrom                  36520  1 ide_cd
ide_disk               17152  0
ide_floppy             18048  0
ide_generic             1920  0
pdc202xx_new            9600  0
aec62xx                 8064  0
alim15x3               12312  0
atiixp                  6544  0
cmd64x                 11596  0
cs5520                  5760  0
cs5530                  6016  0
cy82c693                5512  0
generic                 5632  0
hpt34x                  6016  0
ns87415                 5164  0
opti621                 5252  0
pdc202xx_old           11392  0
piix                   11268  0
rz1000                  3584  0
sc1200                  7808  0
serverworks             9488  0
siimage                12672  0
sis5513                14352  0
slc90e66                6016  0
triflex                 4864  0
trm290                  5252  0
via82cxxx              13488  0
floppy                 62840  0
usb_storage            71488  0
parport_pc             36328  1
parport                38540  2 lp,parport_pc
fbcon                  36480  72
tileblit                2944  1 fbcon
font                    9216  1 fbcon
bitblit                 5760  1 fbcon
vga16fb                12288  1
vgastate                9216  1 vga16fb
vesafb                  9252  0
cfbcopyarea             4352  2 vga16fb,vesafb
cfbimgblt               3200  2 vga16fb,vesafb
cfbfillrect             4736  2 vga16fb,vesafb
softcursor              2944  2 vga16fb,vesafb
usbserial              31728  0
usbkbd                  7808  0
thermal                15120  0
processor              25684  1 thermal
fan                     5384  0
mousedev               12260  1
usbhid                 32416  0
sd_mod                 18456  1
amd74xx                15024  1
ide_core              148932  29 ide_cd,ide_disk,ide_floppy,ide_generic,pdc202xx_new,aec62xx,alim15x3,atiixp,cmd64x,cs5520,cs5530,cy82c693,generic,hpt34x,ns87415,opti621,pdc202xx_old,piix,rz1000,sc1200,serverworks,siimage,sis5513,slc90e66,triflex,trm290,via82cxxx,usb_storage,amd74xx
sata_nv                10756  4
libata                 52744  1 sata_nv
scsi_mod              143984  3 usb_storage,sd_mod,libata
ehci_hcd               31752  0
ohci_hcd               20228  0
evdev                  10496  0
unix                   28728  616

```

---

### Post by Antrix on 2006-03-23
Slight update...

Having realised I'll want the latest GNOME and all that I'm now downloading the bleeding edge Dapper flight 5 ;) I've chosen the x86 CD over amd64 as the advantages offered by 64bit system are not as important to me as software availability (win32 codecs, flash etc etc).

If dapper goes wrong I can always fall back on my trusty breezy dvd.

Wish me luck, the install is going ahead tonight.

---

### Post by rhomsy on 2006-03-23
[QUOTE=deadgobby]yes, you may want to try the new Drapper Flight CD. 
 Here is the news on Drapper.
The controversial decision of the Ubuntu developers to postpone the final release of Dapper Drake by six weeks has met with mixed reactions. Although the decision-making process was democratic and the reasons for the proposed delay sound, the decision has its critics. 
Gobby[/QUOTE]

Are you sure the release of Dapper has been pushed back 6 weeks?  I knew it was being contemplated, but I never found a decision.  That's unfortunate since the packages in breezy are getting a little dated.  I wish they at least updated the packages in breezy (Evolution and Firefox) since we may now have to wait another month and a half.

---

### Post by Antrix on 2006-03-23
Dapper flight 5 failed for me. X is broken (possibly quite badly).


When GDM tried to start i get a blue-screened ncurses interface telling me that X failed to start as usual, but if i want to view the error log. I clicked Yes.

It was a one-liner telling me something like /etc/X11/X not existing (didnt use this word, but it was related to this file)... Hmm ok I thought...

I went to /etc/X11 and did a list... xorg.conf didnt exist (as this is probably created on first startup of X), but neither did X.

I tried creating a symbolic link from /etc/X11/X -> /usr/bin/X ... This time something happened and I had hard drive activity when i tried to start GDM, but it still errored out and i got some kind of infinate loop with lines comming down my screen. I could switch with ctrl alt fx, but as its late and im tired i decided just to put reboot and put breezy on.

Anyway, just thought I'd let you know how my first encounter with flight5 went... Pretty much down the pan ;)

I would usually write down all error messages and save log files to file a bug but i simply dont have the time right now, sorry ubuntu community - i will make up for it later.

---

### Post by Antrix on 2006-03-24
For some bizarre reason the "radeon" driver worked for me in full resolution in the live session but NOT in the real install. Max i could get was something like 800x600. (This is BREEZY by the way)

So i've installed the official ati.com driver as i'll need the 3D acceleration later on anyway. Works FINE now after a while fiddling around getting it to work. I used the guide on the forums EXCEPT i did NOT bother getting rid of the atheros/madwifi package as the author suggests (was simply to lazy). Things seem ok though. I DID have to comment out the line in my xorg.conf as i'm running amd64.

Tell you what, I miss nvidia so much already. ATI is a lot of bloody hassle (!!!!), and I hear I won't get full 3D performance out of my card even with the official drivers.

Just happy i got the basics working now. Tomorrow I'll be making sure my audio + capture works properly.

Cya for now, thanks to all who responded. One thing... Somebody MUST update the official ATI binary document in the official documentation. It should be replaced by the guide available in forums.

Goodnight :)

---

