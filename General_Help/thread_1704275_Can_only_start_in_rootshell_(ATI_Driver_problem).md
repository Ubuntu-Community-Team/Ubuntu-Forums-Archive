---
title: "Can only start in rootshell (ATI Driver problem)"
date: 2011-03-10
forum: General Help
---

### Post by Call_M on 2011-03-10
It when so well untill I did something stupid...

I wanted to upgrade my ati propriatary driver. So I downloaded it from [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English) installed it. But I all in a sudden had 2 times catalyst control centre. Compiz was not working anymore so I went to: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide)

And I did:
```
$ sudo sh /usr/share/ati/fglrx-uninstall.sh

```
I had a few errors and did a restart. Then I could only login with a command line. Then I did:

```
$ sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
```

restart 
And then I knew... It is broken. 

Now I can only start in safemode and then only a command line with network.

Then I tried to install the driver again with [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide)

however it fails getting the right packages. if I do:
```
$ sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6 dkms libqtgui4 wget execstack libelfg0
```

It says something like: getting something from [http://archive.ubuntu](http://archive.ubuntu) etcetera faild, something strange happend no addres linked to host-name. 

(language is not set to english so something like this)

Than wget [ati driver adres] aslo failes
it says that it cannot find the host adres www2.ati.com

I checked everything for typo's and also did a apt-get update
Further more I did:
```
sudo add-apt-repository "deb http://archive.canonical.com/ maverick partner"
```

Can someone please help me?!

---

### Post by Yellow Pasque on 2011-03-10
Your mistake was trying to install new Catalyst over an old one. The guide specifically says not to do that in the Updating section. I suspect you just have a lingering xorg.conf, so remove your /etc/X11/xorg.conf and then try normal boot.

---

### Post by Call_M on 2011-03-10
> **Temüjin said:**
> Your mistake was trying to install new Catalyst over an old one. The guide specifically says not to do that in the Updating section. I suspect you just have a lingering xorg.conf, so remove your /etc/X11/xorg.conf and then try normal boot.

\\:D/ That did the trick. I also saw later the Updating section. 

Thank you mister!

---

