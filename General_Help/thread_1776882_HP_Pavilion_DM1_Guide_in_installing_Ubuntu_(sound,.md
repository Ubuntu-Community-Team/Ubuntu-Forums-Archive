---
title: "HP Pavilion DM1 Guide in installing Ubuntu (sound, video and wifi fixed!)"
date: 2011-06-06
forum: General Help
---

### Post by buknoii on 2011-06-06
Hi there! I've recently purchased an HP Pavilion DM1 and for sure you experienced the following problems

* Wifi not working
* Video Card not working
* Headphones not working

Anyways regarding with the headphones it works perfectly in Ubuntu 10.04 and not in Ubuntu 10.10, and please if you are using Ubuntu 10.04 and your laptop hibernates you'll be surprised that your headphones won't work. Restarting wont do the fix, you need to restart your alsa-mixer and totally shutdown your laptop.


For the WiFi below are the instruction (**thanks to 6by9.net**)


Go to _[https://build.opensuse.org/package/binaries?package=rt5390sta&project=driver%3Awireless&repository=11.4-update](https://build.opensuse.org/package/binaries?package=rt5390sta&project=driver%3Awireless&repository=11.4-update)_

You'll see 64-bit (x86_64) and 32-bit (i586) packages listed. Download the openSUSE driver package - the source RPM, not the binary package: **rt5390sta-2.4.0.4-7.1.src.rpm**

Open your web browser's download directory and double-click the src RPM. Extract all files into a new directory named openSUSE_rt5390sta_driver

Open a terminal and sudo to root:
sudo su -
cd openSUSE_rt5390sta_driver
tar jxvf 2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO.tar.bz2
cd 2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/
patch -p0 < ../rt5390sta-2.4.0.4-config.patch
patch -p0 < ../rt5390sta-2.4.0.4-WPA-mixed.patch
patch -p0 < ../rt5390sta-2.4.0.4-convert-devicename-to-wlanX.patch
patch -p0 < ../rt5390sta-2.4.0.4-remove-potential-conflicts-with-rt2860sta.patch
patch -p0 < ../rt5390sta-2.4.0.4-return_nonvoid_function.patch
patch -p0 < ../rt5390sta-2.4.0.4-reduce_debug_output.patch
mv RT2860STA.dat RT5390STA.dat
vi os/linux/config.mk

Change HAS_ANTENNA_DIVERSITY_SUPPORT to:
HAS_ANTENNA_DIVERSITY_SUPPORT=y

make
mkdir -p /etc/Wireless/RT5390STA
cp RT5390STA.dat /etc/Wireless/RT5390STA/
cp -i os/linux/rt5390sta.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/
echo rt5390sta >> /etc/modules
echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist.conf
depmod -a




For the Video Card just follow the steps at **_[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)_**

---

### Post by Dafydd on 2011-06-22
> **buknoii said:**
> Hi there! I've recently purchased an HP Pavilion DM1 and for sure you experienced the following problems
* Wifi not working
For the WiFi below are the instruction (**thanks to 6by9.net**)

Thanks for this. followed the instructions (a few errors after make install).

now the wlan0 is recognised. Unfortunately, network manager does not scan probably or show any networks.

The HP Pavilion is a great machine but it's a shame to have to use a wifi key on it. Also I can't get suspend or hibernate to work. That's a real pain.

I want to try OpenSuse as I read on internet somewhere that the HP Pavilion DM1 works better with it but unfortunately OpenSuse wont boot as a USB key on the machine.

---

### Post by Radioactivekid on 2011-07-04
Thank you,
Now I can access my wireless network

---

### Post by gruntboyx on 2011-08-22
just to add my 2cents.  I had to enable and disable the wireless once for this solution to work.  After that everything was smooth sailing.

---

### Post by Imnotroot on 2011-11-10
Thank you!

---

### Post by LucasLinard on 2012-02-26
Opensuse boots on usb stick.
Just change the boot order at bios setup (f10) 


> **Dafydd said:**
> Thanks for this. followed the instructions (a few errors after make install).

now the wlan0 is recognised. Unfortunately, network manager does not scan probably or show any networks.

The HP Pavilion is a great machine but it's a shame to have to use a wifi key on it. Also I can't get suspend or hibernate to work. That's a real pain.

I want to try OpenSuse as I read on internet somewhere that the HP Pavilion DM1 works better with it but unfortunately OpenSuse wont boot as a USB key on the machine.

---

### Post by pushkarmishra on 2012-05-08
Please tell me, is hp dm1 totally compatible with ubuntu??

---

