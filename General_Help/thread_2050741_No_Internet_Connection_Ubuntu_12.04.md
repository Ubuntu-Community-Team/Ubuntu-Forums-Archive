---
title: "No Internet Connection Ubuntu 12.04"
date: 2012-08-31
forum: General Help
---

### Post by Blijfiguurpaul on 2012-08-31
Hello everyone!

I'm from the Netherlands so my English is not very good.
Sorry about that.

I am a absolutely beginner about Ubuntu and linux.
I've succesfully installed Ubuntu 12.04 on my computer.
There's only one problem.
I have no internet connection!
Ubuntu recognises my USB adapter, but I think he has no drivers.
In my case, there's no way to plug an ethernet-kabel in the Computer.

Please, can someone help?

This is my stick:

Sweex Connected Home 150N

What should I do?

---

### Post by ectechnologies on 2012-08-31
Hi,

First, on the top right corner of your screen there is a cog, where you turn the pc off. Click on that and on the drop down menu select system setting.

Then Click Additional Drivers and if there are, let me know which ones are available.

---

### Post by Blijfiguurpaul on 2012-08-31
> **ectechnologies said:**
> Hi,

First, on the top right corner of your screen there is a cog, where you turn the pc off. Click on that and on the drop down menu select system setting.

Then Click Additional Drivers and if there are, let me know which ones are available.

Only that I can install a GPU-driver (videocart)
Nothing else...

---

### Post by steeldriver on 2012-08-31
If you run in a terminal 

```
lsusb
```and / or

```
sudo lshw -C network
```and post the results it should tell us some information about what's inside the stick - then maybe we can figure out what driver it needs

---

### Post by Blijfiguurpaul on 2012-09-01
> **steeldriver said:**
> If you run in a terminal 

```
lsusb
```and / or

```
sudo lshw -C network
```and post the results it should tell us some information about what's inside the stick - then maybe we can figure out what driver it needs

Ok, here's the picture:

[IMG]G:\Terminal.png[/IMG]

Ok, that didn't work. I typ all information from the terminal right here:

paul@ubuntu:~$ lsusb

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 004: ID 177f:0163 Sweex
Bus 001 Device 005: ID 054c:0243 Cony Corp. MicroVault Flash Drive
Bus 003 Device 002: ID 046d:c51b Logitech, Inc. V220 Cordless Optical Mouse for
Notebooks
Bus 003 Device 003: ID 046d:c207 Logitech, Inc. Wingman Extreme Digital 3D
paul@ubuntu:~$ sudo lshw -C network
[sudo] password for paul:
  *-network
        description: Ehternet interface
        product: RTL8111/8168B PCI Express Gigabit Ethernet Controler
        vendor: Realtek Semiconductor Co., Ltd.
        physical id: 0
        bus info: pci@0000:02:00.0
        logical name: eth0
        version: 06
        seriall: 54:04:a6:6b:ba:a9
        size: 10Mbit/s
        capacity: 1Gbit/s
        width: 64 bits
        clock: 33MHz
        capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet phy
sical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
        configruation: autonegotiation=on broadcast=yes driver=r8169 driverversio
n=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no mu
lticast=yes port=MII speed=10Mbit/s
        resoucres: irq:42 ioport:e800(size256) memory: f8fff000-f8ffffff memory:f
8ff8000-f8ffbfff
paul@ubuntu:~$

---

### Post by gandaran on 2012-09-01
> Bus 007 Device 004: ID 177f:0163 Sweex
I think you can get this adapter working, it has a ralink wireless chipset and probably just need to load the right driver.
lets check first if any ralink driver is loaded by posting the output of 
```
lsmod
```
this [one has the same ID 177f:0163]("http://www.wikidevi.com/wiki/Sweex_LW163") as yours so maybe its just a case of choosing either the rt2800usb or rt3370sta driver.

---

### Post by Blijfiguurpaul on 2012-09-01
> **gandaran said:**
> I think you can get this adapter working, it has a ralink wireless chipset and probably just need to load the right driver.
lets check first if any ralink driver is loaded by posting the output of 
```
lsmod
```
this [one has the same ID 177f:0163]("http://www.wikidevi.com/wiki/Sweex_LW163") as yours so maybe its just a case of choosing either the rt2800usb or rt3370sta driver.

yes... that's is a big text, again...
well, here it comes:

paul@ubuntu:~$
Module      **Size**     Used by
nls_iso8859 **12713**    1
nls_cp437   **16911**    1
vfat        **17585**    1
fat         **61512**    1 vfat
bnep        **18281**    2
lp          **17799**    0
rfcomm      **47604**    0
bluetooth   **180104**   bnep, rfcomm
snd_hda_codec_realtek **224066** 1
snd_hda_intel **33733** 3
snd_hda_codec **127706** 2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep **13668** 1 snd_hda_codec
snd_pcm **97188** 2 snd_hda_intel,snd_hda_codec
ppdev **17113** 0
snd_seq_midi **13324** 0
snd_rawmidi **30748** 1 snd_seq_midi
snd_seq_midi_event **14899** 1 snd_seq_midi
snd_seq **61896** 2 snd_seq_midi,snd_seq_midi_event
snd_timer **29990** 2 snd_pcm,snd_seq
snd_seq_device **14540** 3 snd_seq_midi,snd_rawmidi,snd_seq
snd **78855** 15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_cod
ed,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
edac_core **53746** 0
seria_raw **13211** 0
edac_mce_amd **23709** 0
fam15h_power **13115** 0
k10temp **13166** 0
sp5100_tco **13791** 0
i2c_piix4 **13301** 0
soundcore **15091** snd
snd_page_alloc **18529** 2 snd_hda_intel,snd_pcm
joydev **17693** 0
parport_pc **32866** 1
parport **46562** 3 lp,ppdev,parport_pc
asus_atk0110 **18078** 0
mac_hid **13253** 0
usbhid **47199** 0
hid **99559** 1 usbhid
usb_storage **49198** 1
uas **18180** 0
nouveau **774641** 3
ttm **76949** 1 nouveau
drm_kms_helper **46978** 1 nouveau
drm **242038** 5 nouveau,ttm,drm_kms_helper
i2c_algo_bit **13423** 1 nouveau
mxm_wmi **19256** 1 nouveau
wmi **19256** 1 mxm_wmi
video **19596** 1 nouveau
r8169 **62099** 0
pata_atiixp **13204** 1
palu@ubuntu:~$

So, finally done!
The Module is normal, the Size is with a '**B**', and the 'Used by' is also 'normal'.
I hope this helps.

---

### Post by Topsiho on 2012-09-01
Hallo Blijfiguurpaul,

I'm from Holland too, and so I can give you some local information, for just in case your wifi stick refuses to operate even after the help from this great forum:

1. Sometimes new hardware is not yet recognized/supported even by the newest kernels in the newest Ubuntu (kernels contain the drivers). To have the newest kernel be sure to regularly update Ubuntu. Hope you did that, you anyhow should. My experience is that new wifi hardware often is operating well after some months.

2. If you have no luck, you might consider trying other wifi sticks. I use the ICIDU 150N stick, which did not work in the kernels of Ubuntu 10.04, but it does in the kernels of the newer Ubuntu's. One thing: I bought this stick some time ago now and things change fast. ICIDU is sold by many computer shops, such as Mycom and I think Dixons and Vobis.

Topsiho

---

### Post by steeldriver on 2012-09-01
I think gandaran is right, I don't know this particular device but I have an ASUS N13 (Vendor:Subsystem ID 0b05:1784) that apparently uses a Ralink RT3072 chipset and that works with the rt2800usb module

So the question would seem to be why the correct module is not getting loaded - there may be a competing module that we need to blacklist, or you may need to install extra firmware

I'm a bit worried that it does not show up at all in lshw - usually iirc even devices without drivers show up there (but are listed as 'unclaimed'). Maybe that points to firmware? I don't know...

I guess there's no harm in trying

```
sudo modprobe rt2800usb
```

---

### Post by gandaran on 2012-09-02
Blijfiguurpaul
lsmod did not show any ralink driver loaded (was the adapter plugged in?)
if the **sudo modprobe rt2800usb** command did not work then I think you will have to install the RT3370 driver, [URL="http://www.ralinktech.com/en/04_support/support.php?sn=501"]
download here[/URL] (it's the third from the top) the package should have install instructions or download the PDF too.

---

### Post by Blijfiguurpaul on 2012-09-02
> **steeldriver said:**
> I think gandaran is right, I don't know this particular device but I have an ASUS N13 (Vendor:Subsystem ID 0b05:1784) that apparently uses a Ralink RT3072 chipset and that works with the rt2800usb module

So the question would seem to be why the correct module is not getting loaded - there may be a competing module that we need to blacklist, or you may need to install extra firmware

I'm a bit worried that it does not show up at all in lshw - usually iirc even devices without drivers show up there (but are listed as 'unclaimed'). Maybe that points to firmware? I don't know...

I guess there's no harm in trying

```
sudo modprobe rt2800usb
```

i tried the sudo modprobe rt2800usb command, but than it asked me for a password, and then just nothing. i can typ than a new commando. 
it looks like this:

paul@ubuntu:~$ sudo modprobe rt2800usb
[sudo] password for paul: (my password)
paul@ubuntu:~$

that's it...

---

### Post by Blijfiguurpaul on 2012-09-02
> **gandaran said:**
> Blijfiguurpaul
lsmod did not show any ralink driver loaded (was the adapter plugged in?)
if the **sudo modprobe rt2800usb** command did not work then I think you will have to install the RT3370 driver, [URL="http://www.ralinktech.com/en/04_support/support.php?sn=501"]
download here[/URL] (it's the third from the top) the package should have install instructions or download the PDF too.

The adapter was plugged in.
I tried to install the RT3370 driver, but I have no idea how to install it. the read me didn't helped me. i am very new to linux and ubuntu, i don't know how to install something. could you help me with installing the driver?

---

### Post by gandaran on 2012-09-02
> **Blijfiguurpaul said:**
> The adapter was plugged in.
I tried to install the RT3370 driver, but I have no idea how to install it. the read me didn't helped me. i am very new to linux and ubuntu, i don't know how to install something. could you help me with installing the driver?
yes this driver is complicated to install! you can search for webpages with instructions using [COLOR="Red"]ubuntu rt3370[/COLOR] on google search
see if this one helps
[https://help.ubuntu.com/community/WifiDocs/Device/Tenda_W311M](https://help.ubuntu.com/community/WifiDocs/Device/Tenda_W311M)

edit:
maybe you will have to change the part of rt5370sta to rt3370sta in your case, the driver is the same but works for many other adapters too using different modules.

---

### Post by gandaran on 2012-09-02
> **Blijfiguurpaul said:**
> i tried the sudo modprobe rt2800usb command, but than it asked me for a password, and then just nothing. i can typ than a new commando. 
it looks like this:

paul@ubuntu:~$ sudo modprobe rt2800usb
[sudo] password for paul: (my password)
paul@ubuntu:~$

that's it...
the only thing supposed to happen was the adapter work after running command, did you look up in the network manager panel icon for detected wireless networks after waiting a minute or two?
you can also check with **lsmod** if the command loaded rt2800usb.

---

### Post by gandaran on 2012-09-02
there is another option you could try, install the compact-wireless package, maybe this package has better up to date drivers.
```
sudo apt-get install linux-backports-modules-cw-3.3-precise-generic-pae
```

---

### Post by steeldriver on 2012-09-02
yes if the modprobe command didn't give any error messages that should mean that it worked (at least as far as loading the driver module)

if it loaded i.e.

```
lsmod | grep 'rt2800'
```produces some output, but your device still does not show up, then the next thing I would try is the 'backports' package

As well, if rt2800usb *is* the correct driver, and it *is* loadable, then we need to figure out why it's not getting loaded automatically.

---

### Post by Blijfiguurpaul on 2012-09-02
> **gandaran said:**
> the only thing supposed to happen was the adapter work after running command, did you look up in the network manager panel icon for detected wireless networks after waiting a minute or two?
you can also check with **lsmod** if the command loaded rt2800usb.

no, it didn't worked. i'm going to check if the 'lsmod' command worked

---

### Post by Blijfiguurpaul on 2012-09-02
> **gandaran said:**
> there is another option you could try, install the compact-wireless package, maybe this package has better up to date drivers.
```
sudo apt-get install linux-backports-modules-cw-3.3-precise-generic-pae
```

when i put that code into the terminal, he wants to download data from the internet...

---

### Post by Blijfiguurpaul on 2012-09-02
> **Blijfiguurpaul said:**
> no, it didn't worked. i'm going to check if the 'lsmod' command worked

no, also the 'lsmod' command did not worked

---

### Post by gandaran on 2012-09-02
> **Blijfiguurpaul said:**
> when i put that code into the terminal, he wants to download data from the internet...
yes you need a wired internet connection.

---

### Post by Blijfiguurpaul on 2012-09-02
> **gandaran said:**
> yes you need a wired internet connection.

sorry, but I haven't. our router hasn't a wired connection...
yes, it's weird... do you have any other solution?

---

### Post by gandaran on 2012-09-03
download the file from [ubuntu packages]("http://packages.ubuntu.com/precise/allpackages"), scroll down till you find the package (linux-backports-modules), choose the right (architecture) .deb for your system then on ubuntu click to install, also the package I mentioned requires the install of another package first (the real one with drivers), it will tell you which one when you try to install, I don't know which kernel you have on Ubuntu so I give you that code that would have pulled the right dependency.

---

### Post by Blijfiguurpaul on 2012-09-04
> **gandaran said:**
> download the file from [ubuntu packages]("http://packages.ubuntu.com/precise/allpackages"), scroll down till you find the package (linux-backports-modules), choose the right (architecture) .deb for your system then on ubuntu click to install, also the package I mentioned requires the install of another package first (the real one with drivers), it will tell you which one when you try to install, I don't know which kernel you have on Ubuntu so I give you that code that would have pulled the right dependency.

ehm... it did not worked. isn't there a general driver for the most common wifi adapters?

when I try to install, the Ubuntu Software Center gives a error.
i don't understand it...

---

### Post by gandaran on 2012-09-04
> **Blijfiguurpaul said:**
> ehm... it did not worked. isn't there a general driver for the most common wifi adapters?

when I try to install, the Ubuntu Software Center gives a error.
i don't understand it...
what was the error? maybe the package list needs to be updated first but you don't have a wired working internet so it's a no go situation!
and no there's no common driver (or the common Ralink brand driver would be the rt2800usb if your adapter can work with it!)
also you will need an internet connection even for installing the other ralink website driver as you will have to install compiling tools first!
the best chance was the compact-wireless package with the rt2800usb module and it should install easy if you can find the right corresponding package for the kernel in use and in fact its easy to find it in ubuntu packages website, you just follow numbers.
well,Blijfiguurpaul I'm sorry it didn't work out, all I can say now is go for an adapter guaranteed to work out of the box, you can find cheep ones on ebay for about 5/10 euros, just look for the ones with the penguin icon.
 [http://www.ebay.co.uk/sch/i.html?_trksid=p5197.m570.l1311&_nkw=wireless+adapters&_sacat=0](http://www.ebay.co.uk/sch/i.html?_trksid=p5197.m570.l1311&_nkw=wireless+adapters&_sacat=0)
[http://www.ebay.co.uk/sch/i.html?_odkw=wireless+adapters&_osacat=0&_trksid=p2045573.m570.l1313&_nkw=linux+wireless+adapters&_sacat=0](http://www.ebay.co.uk/sch/i.html?_odkw=wireless+adapters&_osacat=0&_trksid=p2045573.m570.l1313&_nkw=linux+wireless+adapters&_sacat=0)

---

### Post by Blijfiguurpaul on 2012-09-11
> **gandaran said:**
> what was the error? maybe the package list needs to be updated first but you don't have a wired working internet so it's a no go situation!
and no there's no common driver (or the common Ralink brand driver would be the rt2800usb if your adapter can work with it!)
also you will need an internet connection even for installing the other ralink website driver as you will have to install compiling tools first!
the best chance was the compact-wireless package with the rt2800usb module and it should install easy if you can find the right corresponding package for the kernel in use and in fact its easy to find it in ubuntu packages website, you just follow numbers.
well,Blijfiguurpaul I'm sorry it didn't work out, all I can say now is go for an adapter guaranteed to work out of the box, you can find cheep ones on ebay for about 5/10 euros, just look for the ones with the penguin icon.
 [http://www.ebay.co.uk/sch/i.html?_trksid=p5197.m570.l1311&_nkw=wireless+adapters&_sacat=0](http://www.ebay.co.uk/sch/i.html?_trksid=p5197.m570.l1311&_nkw=wireless+adapters&_sacat=0)
[http://www.ebay.co.uk/sch/i.html?_odkw=wireless+adapters&_osacat=0&_trksid=p2045573.m570.l1313&_nkw=linux+wireless+adapters&_sacat=0](http://www.ebay.co.uk/sch/i.html?_odkw=wireless+adapters&_osacat=0&_trksid=p2045573.m570.l1313&_nkw=linux+wireless+adapters&_sacat=0)

ehm... i think i don't need help anymore.
my network adapter just died.
he does nothing and windows does not recognise hime.
also if i run lsmod he doesn't recognise it.
so i'm going to buy a stick which works also in linux
thank you for you help everyone!
this is a great forum
it's my first question on this forum, and i get so many help!
thank you everyone!!!

---

