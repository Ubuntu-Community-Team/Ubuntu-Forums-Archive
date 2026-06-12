---
title: "Toshiba(?)Problem in 11.04 got worse with  11.10 upgrade"
date: 2011-10-20
forum: General Help
---

### Post by davidshelton on 2011-10-20
So I've just made the jump from Windows to Ubuntu(please remember I am a newbie!). My system is as follows : 
david@david-Satellite-C655:~$ sudo lshw -short
[sudo] password for david: 
H/W path           Device      Class       Description
======================================================
                               system      Notebook
/0                             bus         Portable PC
/0/0                           memory      1MiB BIOS
/0/13                          memory      3GiB System Memory
/0/13/0                        memory      2GiB SODIMM DDR3 Synchronous 800 MHz 
/0/13/1                        memory      1GiB SODIMM DDR3 Synchronous 800 MHz 
/0/1e                          processor   Intel(R) Celeron(R) CPU          900 
/0/1e/1f                       memory      1MiB L2 cache
/0/1e/21                       memory      32KiB L1 cache
/0/20                          memory      32KiB L1 cache
/0/100                         bridge      Mobile 4 Series Chipset Memory Contro
/0/100/2                       display     Mobile 4 Series Chipset Integrated Gr
/0/100/2.1                     display     Mobile 4 Series Chipset Integrated Gr
/0/100/1a                      bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1a.1                    bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1a.7                    bus         82801I (ICH9 Family) USB2 EHCI Contro
/0/100/1b                      multimedia  82801I (ICH9 Family) HD Audio Control
/0/100/1c                      bridge      82801I (ICH9 Family) PCI Express Port
/0/100/1c/0        eth0        network     AR8152 v1.1 Fast Ethernet
/0/100/1c.1                    bridge      82801I (ICH9 Family) PCI Express Port
/0/100/1c.1/0      wlan0       network     AR9285 Wireless Network Adapter (PCI-
/0/100/1c.4                    bridge      82801I (ICH9 Family) PCI Express Port
/0/100/1d                      bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1d.1                    bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1d.2                    bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1d.3                    bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1d.7                    bus         82801I (ICH9 Family) USB2 EHCI Contro
/0/100/1e                      bridge      82801 Mobile PCI Bridge
/0/100/1f                      bridge      ICH9M LPC Interface Controller
/0/100/1f.2        scsi1       storage     ICH9M/M-E SATA AHCI Controller
/0/100/1f.2/0      /dev/sda    disk        250GB TOSHIBA MK2565GS
/0/100/1f.2/0/1    /dev/sda1   volume      230GiB EXT4 volume
/0/100/1f.2/0/2    /dev/sda2   volume      2938MiB Extended partition
/0/100/1f.2/0/2/5  /dev/sda5   volume      2938MiB Linux swap / Solaris partitio
/0/100/1f.2/1      /dev/cdrom  disk        DVDRAM GT30N
/0/100/1f.2/1/0    /dev/cdrom  disk        
/0/100/1f.3                    bus         82801I (ICH9 Family) SMBus Controller
/1                             power       OEM_Define4


I first installed 11.04 from W7 via Wubi. Got caught by buggy installation wizard crashing at keyboard language options. After crashing and reninstalling a few times found I just needed to leave it at default and change later. Ok no problem. Installed 11.04 then when doing first boot up from hdd the whole thing crashed during boot up a few times. No error messages just blank screen or purple. Then after manual reset a couple of times finally got GRUB(I think) screen and got it to run using "earlier version". Worked pretty ok but sometimes slow and dvd playback had choppy video and audio on media player and VLC despite latest codecs etc installed. I could live with it so didn't try to mess around at all and jumped at the chance to upgrade to 11.10 hoping that this problem might disappear. Upgrade went ok and again on first reboot whole system crashed at a blank screen. Couple of reboots later got back to grub screen and chose "earlier version"(what is that anyway?). So once that was achieved got into the snazzy new 11.10 version interface only it's super sloooooow! Scrolling down a firefox page, more than a couple of pages opened and the cpu redlines and the system bogs down so badly I have to walk away for a couple of minutes to let it recover. DVD super choppy again  and even youtube vid is super choppy and some program menus pages appear with a very visible refresh rate as it loads. Just typing this there is a 2 second plus lag between keystroke and letter appearing. Elsewhere it becomes impossible to type anything because of the lag. Could this be the display driver? It seems anything to do with the display is running through the CPU only somehow and that's why it bogs so easily ie with page scrolling, video playback etc Sorry to be so long winded I just wanted to be thorough. I hope someone can help because after hours of searching i haven't found and answer to this problem. :popcorn:

---

### Post by davidshelton on 2011-10-21
Just did a full memory test and have gone through GRUB a couple of times and am now running the latest version. 3.0.0.12(?). Was that the default before unless a crash brought me to GRUB to choose otherwise?? Somehow 11.10 is running like a charm today(so far!). Did that process cause it to apply some changes perhaps that have fixed things? :confused: though happy it's working today. I was ready to give up on Ubuntu and go back to W7....

---

### Post by davidshelton on 2011-10-21
Ok! So I did install the i965 VA driver but that was about 4-5 reboots ago. Could it have taken this long to apply those changes?? Still working fine .... for now :confused:

---

### Post by davidshelton on 2011-10-26
So every other boot up the machine is slow and can bog down a bit. I've had one crash on boot up also....
Any ideas then?

---

### Post by oldtimer7777 on 2011-10-27
> **davidshelton said:**
> So every other boot up the machine is slow and can bog down a bit. I've had one crash on boot up also....
Any ideas then?

I'm running the previous version of that Toshiba you have there...  I am sticking with 10.10 for now on that machine, but 11.10 just isn't ready for my Toshiba yet.  

Hopefully that saves you some time.  Use 10.10 and see if this still happens.. It will probably be fine after that.

---

### Post by Rodney9 on 2011-10-27
A lighter resource operating system like Lubuntu or Xubuntu would make that machine run much faster.
Lubuntu runs so fast on my Toshiba L500 laptop.

---

### Post by davidshelton on 2011-11-01
Thanks for the helpful advice. I was beginning to wonder if anyone was going to reply. Oddly enough the problem is intermittent. Sometimes youtube works and even hd streaming and even dvd. Other times it's different shades of not working or completely impossible to see video and basic OS functions are super slow.... How do I roll back to Lubuntu or earlier version of Ubuntu without losing programs and settings? I will post any new developments. I hope it helps the next person....

---

