---
title: "Uninstall/Reinstall sound drivers?"
date: 2009-10-25
forum: General Help
---

### Post by munkifisht on 2009-10-25
I couldn't find anything of use for this issue. I was trying to get the drivers for my sound card (Realtek ALC1200 as inbuilt on the ASUS P5Q Pro board). Anyway, there is a file on the Asus site for dirver updates, but I think it is based on an older version of ALSA that had alsaconf inc'd. The install didn't complete and the old sound drivers seem to have been ruined. Now I think a reinstall is the best option. Total Newb here too.

---

### Post by munkifisht on 2009-10-26
Bump

---

### Post by phillw on 2009-10-26
> **munkifisht said:**
> I couldn't find anything of use for this issue. I was trying to get the drivers for my sound card (Realtek ALC1200 as inbuilt on the ASUS P5Q Pro board). Anyway, there is a file on the Asus site for dirver updates, but I think it is based on an older version of ALSA that had alsaconf inc'd. The install didn't complete and the old sound drivers seem to have been ruined. Now I think a reinstall is the best option. Total Newb here too.

Can you give your version / flavour of ubuntu  & I'll go and have a dig around for you.

Phill.

---

### Post by munkifisht on 2009-10-26
The Version number is 9.10, but some research has me now thinking that what I should be doing is a manual install, but I can't find anyone as Linux thick as me, so the explinations I'm seeing are a little advanced.

Firstly, there are two folders in the extracted driver. One is Linux, the other RHEL4 (that's red hat right?). Well runing ./install from the Linux folder brings up a dialogue which does not find any devices. Running the red hat one brings finds my graphics card and an intel 82801ji controller, which I think is for the sound card. 

So RTFM time:

```


Linux Source Code for ALC audio codec
Support Codec list:
====AC97 Codec=====
ALC100,100P
ALC200,200P
ALC650D
ALC650E
ALC650F
ALC650
ALC655
ALC653
ALC658
ALC658D
ALC850
ALC101
ALC202
ALC250
ALC203

====HD Audio codec ====
ALC260
ALC262
ALC660
ALC861
ALC880
ALC882
ALC883
ALC885
ALC888

Installation:
This Source Code is from www.alsa-project.org.
Installation notice:
1.It must have GCC compiler in your OS.
2.Kernel source code is the necessary for driver compile.

For driver installation, please follow below steps. 

Automatic install:
execute

  ./install

Manual install:
Step 1. unzip source code
        tar xfvj alsa-driver-1.0.xx.tar.bz2

Step 2. Turn on sound support (soundcore module, default turn on)

Step 3. Complied source code and install the driver
    a. cd alsa-driver-1.0.xx
    b. ./configure
    c. make
    d. make install
    e. ./snddevices

Step 4. Install ALSA Lib
        a. tar jxvpf alsa-lib-1.0.xx.tar.bz2
        b. cd alsa-lib-1.0.xx
        c. ./configure 
        d. make
        e. make install

Step 5. Install ALSA Utility
        a. tar jxvpf alsa-utils-1.0.xx.tar.bz2
        b. cd alsa-utils-1.0.xx
        c. ./configure
        d. make
        e. make install

Step 6. Run ALSA auto configuration
        ./alsaconf

Step 7. Use the alsamixer the disable mute (All audio line default is mute)
        *Must to compile and to install the ALSA library and utility. (Use automatic install is already installed)
        excute alsamixer

Note:     1. The most detail information, can refer the alsa-kernel/Documenttation/ALSA-Configuration.txt in the azx-021705.tar.bz2.
    2. Kernel Version must be 2.2.14 or later.
    3. All mixer channels are muted by default. You must use a native
        or OSS mixer program to unmute appropriate channels.
    4. If can not compile the source code, try to rename the /usr/src/linux-2.x -> /usr/src/linux.
    5. The driver added to support the SPDIF functoin.     
    6. a. You can download the alsa-lib-1.0.9 and alsa-utils-1.0.9a form the www.alsa-project.org, then unzip and install them. 
       b. Suggest use "alsamixer" to control mixer function.
       c. Used "alsaconf" can autodetect which drive you need to install (step 4).     
        7. SUSE Distribution must install the ncurses package. 
```

I am alreddy stuck on step 2. 

Typeing ```
lspci -nn
```

I get

```
00:00.0 Host bridge [0600]: Intel Corporation 4 Series Chipset DRAM Controller [8086:2e20] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 4 Series Chipset PCI Express Root Port [8086:2e21] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4 [8086:3a37]
00:1a.1 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5 [8086:3a38]
00:1a.2 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6 [8086:3a39]
00:1a.7 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 [8086:3a3c]
00:1b.0 Audio device [0403]: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller [8086:3a3e]
00:1c.0 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1 [8086:3a40]
00:1c.4 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 5 [8086:3a48]
00:1c.5 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6 [8086:3a4a]
00:1d.0 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1 [8086:3a34]
00:1d.1 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2 [8086:3a35]
00:1d.2 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3 [8086:3a36]
00:1d.7 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 [8086:3a3a]
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 90)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller [8086:3a16]
00:1f.2 IDE interface [0101]: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller [8086:3a20]
00:1f.3 SMBus [0c05]: Intel Corporation 82801JI (ICH10 Family) SMBus Controller [8086:3a30]
00:1f.5 IDE interface [0101]: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller [8086:3a26]
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV770 LE [Radeon HD 4800 Series] [1002:944c]
01:00.1 Audio device [0403]: ATI Technologies Inc HD48x0 audio [1002:aa30]
02:00.0 Ethernet controller [0200]: Attansic Technology Corp. L1e Gigabit Ethernet Adapter [1969:1026] (rev b0)
03:00.0 IDE interface [0101]: Marvell Technology Group Ltd. 88SE6121 SATA II Controller [11ab:6121] (rev b2)
05:03.0 FireWire (IEEE 1394) [0c00]: Agere Systems FW323 [11c1:5811] (rev 70)

```

At the moment I am looking at this to try and pin down the problem: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
But with no luck as yet

---

### Post by munkifisht on 2009-10-26
Ok, I have working sound again, but there are still loads of features of my sound card that are not working, and I can't seem to figure them out. I can't seem to get Alsamixer to run, despite Alsa-Utils being installed. 

When I try to run from the command line it I get an error:

$ alsamixer
alsamixer: relocation error: alsamixer: symbol snd_mixer_selem_is_enum_capture, version ALSA_0.9 not defined in file libasound.so.2 with link time reference

$ amixer
Simple mixer control 'Master',0
amixer: relocation error: amixer: symbol snd_mixer_selem_is_enum_playback, version ALSA_0.9 not defined in file libasound.so.2 with link time reference

---

### Post by Shreshtha on 2009-12-11
I too did the same mistake of installing the driver bundled with P5Q-C mobo. After fresh installation of ALSA from source and rebooting, atleast Ubuntu 9.10 now recognizes the sound card (aplay -l) and "lspci -v" it says its using  snd-hda-intel kernel module. But while restarting the service "sudo /etc/init.d/alsa-utils restart" it gives following failure - 

 * warning: 'alsactl store' failed with error message 'alsactl: relocation error: alsactl: symbol snd_ctl_elem_info_is_tlv_readable, version ALSA_0.9 not defined in file libasound.so.2 with link time reference'...

Now - No sound.
Please help.

---

### Post by joes7 on 2009-12-11
Applications->System->Hardware / Drivers

---

### Post by iamgeniusrnti on 2009-12-11
> **munkifisht said:**
> Ok, I have working sound again, but there are still loads of features of my sound card that are not working, and I can't seem to figure them out. I can't seem to get Alsamixer to run, despite Alsa-Utils being installed. 

When I try to run from the command line it I get an error:

$ alsamixer
alsamixer: relocation error: alsamixer: symbol snd_mixer_selem_is_enum_capture, version ALSA_0.9 not defined in file libasound.so.2 with link time reference

$ amixer
Simple mixer control 'Master',0
amixer: relocation error: amixer: symbol snd_mixer_selem_is_enum_playback, version ALSA_0.9 not defined in file libasound.so.2 with link time reference

That happened to me too.  Just use synaptics and completely purge Alsa.  There is one problem though--my sound still wont work.

---

### Post by falconindy on 2009-12-11
Sure, purging ALSA means that Pulse no longer has a way to communicate with the hardware. You **need** ALSA or OSS installed.

---

