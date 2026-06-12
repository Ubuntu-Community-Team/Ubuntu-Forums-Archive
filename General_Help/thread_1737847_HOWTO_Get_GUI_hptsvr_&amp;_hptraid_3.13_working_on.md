---
title: "HOWTO: Get GUI hptsvr &amp; hptraid 3.13 working on Ubuntu"
date: 2011-04-23
forum: General Help
---

### Post by AllGamer on 2011-04-23
HighPoint RAID Management Console runs properly on Ubuntu Desktop 10.10

After several failed attempts to install/use the CLI or WEB version of the RocketRaid Management software, the GUI version is the only one that actually works without causing broken installs or other problems in Ubuntu.

Download the latest version of the driver currently 3.13
```
http://www.highpoint-tech.cn/BIOS_Driver/HRM/Linux/GUI-Linux-3.13-4-1214.tgz
```

Extract the tar file, you should get 4 RPM files + README.txt
**32bit**
hptraid-3.13-3.i586.rpm
hptsvr-3.13-4.i586.rpm
**64bit**
hptraid-3.13-3.x86_64.rpm
hptsvr-3.13-4.x86_64.rpm

Next install **alien**, if it's not installed already run
```
sudo apt-get install alien
```

Now run alien to convert the RPM to DEBian packages

example:
```

sudo alien -d hptraid-3.13-3.i586.rpm
sudo alien -d hptsvr-3.13-4.i586.rpm

```

now before you go and execute dpkg -i <insert package name .deb>, you have to make sure your card is listed within **/etc/hptcfg** which usually is the same as the file name of the driver .ko file 
rr174x.ko = rr174x
rr26xx.ko = rr26xx

example:
```

rr174x
rr26xx

```

Note: if you have more than one RocketRaid installed you should have see both of them listed. However only one driver is required per model.

The installation sequence is important else you'll get errors, make sure you install the **hptraidconf** (hptraid) before the **hptsvr**
```

sudo dpkg -i hptraid-3.13-3.i586.deb
sudo dpkg -i hptsvr-3.13-4.i586.deb

```

Right after the install you can see the **HighPoint RAID Management Console** in the Applications menu, but it will dissapear after a system reboot.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=189846&stc=1&d=1303615882[/IMG]

To execute it via termnial just run

```
sudo hptraid
```

it will fail to run without sudo

---

### Post by lantzanders on 2011-04-29
Thank you for this guide!

I would like to add that on Ubuntu 10.10 Desktop 64bit the installer doesn't make an alias for hptraid so it must be started from /usr/share/hpt/hptraid-3.13/ by running ./htpraid.

Also hptsvr must be manually started on my system before this.


Just in case anyone has the same problem:
I got stuck on installing the CLI management tool for this raidcard because hptraidconf would fail during the installation and mess up all future use of apt-get/dpkg, until i found this [http://ubuntuforums.org/showthread.php?t=455541](http://ubuntuforums.org/showthread.php?t=455541). Basically go in to /var/lib/dpkg/status and remove anything that has anything do to with hptraidconf.

---

### Post by iokhahon on 2011-08-06
Thank you for this guide, I followed it carefully, however, I still have a problem getting htpsvr to start (sudo hptsvr) and I hope someone can suggest ideas for problem determination.

I am using the Highpoint Rocket Raid 622 which came with the Sans Digital TowerRAID TRM8.
I am running Ubuntu 10.10 32bit

When I type sudo hptsvr I get the message "Driver is not loaded.", the driver (which was loaded with modprobe rr62x and the name placed in /etc/modules) is indeed loaded and functional

I am able to start the client UI successfully with the command sudo /usr/share/hpt/hptraid-3.13/hptraid
Be sure you create a member in /etc called hptcfg, this member should contain a single line of text with the name of the device driver for your particular card. This can be automated as follows :-

$sudo -i
#echo `lsmod | grep rr | grep -v scsi | awk '{print $1}'` > /etc/hptcfg

You should now be able to start the server successfully.

---

### Post by sparky3387 on 2011-08-12
Just thought I would let people know how to get the WebGUI working if they desire (please note it must be in this order - and that WebGUI does not load unless CLI has been installed - it must be something in the /usr/share folder as well as /etc/hpt.ini that stops webgui loading):

cd /usr/src
wget [http://www.highpoint-tech.cn/HRM/Linux/WebGUI-Linux-v1.4-14-100630.tgz](http://www.highpoint-tech.cn/HRM/Linux/WebGUI-Linux-v1.4-14-100630.tgz)
wget [http://www.highpoint-tech.cn/BIOS_Driver/GUI/linux/CLL/CLI-Linux-3.5-100701.tgz](http://www.highpoint-tech.cn/BIOS_Driver/GUI/linux/CLL/CLI-Linux-3.5-100701.tgz)
sudo tar xvfz CLI-Linux-3.5-100701.tgz
sudo tar xvfz WebGUI-Linux-v1.4-14-100630.tgz
cd CLI-Linux-3.5-100701/deb/

/* THE DEB PACKAGES HERE ARE SEVERLY BROKEN */
ar xv hptraidconf_3.5_i386.deb
tar xvfz data.tar.gz
cp -rv usr/* /usr/

ar xv hptsvr_3.13-7_i386.deb
tar xvfz data.tar.gz
cp -rv share/* /usr/share/
cp -rv usr/* /usr/

cd WebGUI-Linux-v1.4-14-100630
sudo alien -d --scripts hptsvr-https-1.4-14.i386.rpm
sudo dpkg -i hptsvr-https_1.4-15_i386.deb

vi /etc/hpt.ini
serverport      7402
eventport       7403
remoteaccess    1
alarmenabled    1
hdtempthreshold 140
autorebuild     0
continuerebuildonerror  0
rebuildpriority 50
spindownidlediskminutes 0
userauth        1
httpSSL 0
curhttpSSL      0
connectionoptionsconfig 1

It seems SSL is broken, I have not tried installing SSL packages because my WebGUI is not outside facing.

This is using the Rocketraid 2320.

---

### Post by aykayross on 2011-09-03
I have Ubuntu 11.04 on an Intel i7 platform and I have tried all the steps in this thread and still cannot get the RocketRAID 2320 to work.

Is there anyone out there who has installed this on 11.04 using the 64 bit drivers.

I have tried using the suggestions in this thread, but still not much joy.

Any ideas, or do I look for a hardware raid device that is certified for use on Ubuntu 11.04?
Or horror of horrors do I install Windows 7?



:confused:

---

### Post by sparky3387 on 2011-09-17
> **aykayross said:**
> I have Ubuntu 11.04 on an Intel i7 platform and I have tried all the steps in this thread and still cannot get the RocketRAID 2320 to work.

Is there anyone out there who has installed this on 11.04 using the 64 bit drivers.

I have tried using the suggestions in this thread, but still not much joy.

Any ideas, or do I look for a hardware raid device that is certified for use on Ubuntu 11.04?
Or horror of horrors do I install Windows 7?



:confused:

I got mine to work by doing this:

[https://help.ubuntu.com/community/RocketRaid#Source_modifications_required_in_11.04]("https://help.ubuntu.com/community/RocketRaid#Source_modifications_required_in_11.04")

---

### Post by randknu on 2011-12-25
Has anyone gotten any highpoint raid management tool to work with 2 different cards?

I have a rocketraid 2340 and a 2320 and i tried listing them as
```
rr2340
rr232x
```
in /etc/hptcfg

but that does not work, only the first card appear. If i switch them around, the other card appers.

Tried contacting highpoint support and they told me it was impossible...???? not even a workaround... 

So if i want to manage the other card i have to change hptcfg and restart.... It's a server, it's not supposed to be restarted all the time.

---

### Post by doola on 2012-04-17
Originally Posted by aykayross  
I have Ubuntu 11.04 on an Intel i7 platform and I have tried all the steps in this thread and still cannot get the RocketRAID 2320 to work.

Is there anyone out there who has installed this on 11.04 using the 64 bit drivers.

I have tried using the suggestions in this thread, but still not much joy.

Any ideas, or do I look for a hardware raid device that is certified for use on Ubuntu 11.04?
Or horror of horrors do I install Windows 7?

Highpoint needs better support rather than just email. Through great number of fails and pains even sending the Host Adapter back to them I got it to work.....this is how

When you install the module make sure you get the specified module for your distro I used Ubuntu 10.10 from highpoint....for some reason you cant download it from the site, you have to request it  via their web support.

Use modprobe to add the module to the kernel "modprobe rr272_1x"
Do lsmod to verify the driver exist "lsmod | grep rr272_1x"

Follow their suggested installation method.

Except when you start to make the .deb package from the .rpm with alien do "alien -d --scripts hptsvr-https-1.4-14.x86_64.rpm" Then go to install the WebGUI-Linux-1.4-14-100917.tgz. This should get you up and running

---

### Post by gbrowning on 2012-08-09
Got my highpoint 2720 in the mail.  Have an EVGA X58 motherboard which only supports SATA 2 and USB 2.  Upgrading to  SATA 3 via this board and pciex8. ALSO ugrading to USB 3 with a different host card.
     The 3 SATA drives, including my boot drive, were unplugged from the mother board  attached them to the 2720 card via an SAS to SATAx4 breakout cable.  The whole system booted up without a glitch and and is now running the drives as Legacy drives.  There is a big difference in drive performance. No additional drivers, no additional software. The first objective was achieved with little work.
     The next objective is to get the GUI working to make setting up RAID easier. The eventual goal is to have Ubuntu running on a new SSD with all the files sitting on a 2 disk RAID 1 with a third disk as back-up.
     There is a lot to learn.  First is to get the Highpoint card BIOS flashed to newest version,  will try that in a few moments.

      The

---

### Post by gbrowning on 2012-08-14
Several Methods have been attempted to get the Highpoint BIOS flashed to the latest release and all have failed to this point.
Somehow DOS refuses to work on this system.  Can boot to DOS from CD, can Boot to DOS from USB but cannot run any commands or access any media other than the native DOS files.
     ISOMaster, Balder, Freedos, unetbootin, DOS 6.22., virtualbox.  This remains an enigma.

---

