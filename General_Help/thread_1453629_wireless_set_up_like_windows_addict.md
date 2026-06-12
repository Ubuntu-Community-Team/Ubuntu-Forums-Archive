---
title: "wireless set up like windows addict?"
date: 2010-04-13
forum: General Help
---

### Post by no_ordinary_funace on 2010-04-13
Hi,

Just installed karpet kaolaua, but can't seem to get the wireless detection to work in an area where I know there be wireless signals happening.

I did a lot of searching and downloaded ndiswrapper common, utilities, tdk or whatever the hell it's called, but still nada.

I actually clicked on the question mark icon in ubuntu and did a search for wireless. It tells me to look for the icon of two little computers dancing together in the upper right hand of the screen, but I don't see such happy copulation on my screen (just a crappy little picture of an antenna with no singnal which only gives me a choice of "wired network" when I right click it). It also tells me to make sure my wireless device is "turned on".  Well, as much as I dance in front of my computer, I still get the same negative results.  Maybe I should have shaved first.

However, in windows the wireless device (automatically) detects wireless signals around me. 

So what I want to know is, how do I coerce Ubuntu to also detect unsecured wireless networks around me, which I can legitimately leech off of, in a good way? (until I learn more about aircrackrocking, that is, but for tentesting only).

Umm, as far as I know, I have a "mobile intel 945 GSE Express chipset" AND a "Ralink RT 3090 wireless 802.11n"  depending on which source I check.  Apparently they are the same thing.

Thanks.

---

### Post by Scunnered on 2010-04-13
Assuming that you are working with 9.10 you should see next to the sound icon four bars rising from left to right.  If you right click on them you should see Enable Networking and Enable Wireless. Ensure that these are both ticked.

If you then left click on the bars you should be offered wireless networks available to you and you then select whichever you wish.  I think from memory you will be asked for a password which was in my case the one I agreed with my ISP when initially setting up my broadband access.  I am not too sure if you will be asked for this if you are availing your self of an unsecured network bit if asked suggest that you offer up your login one and hope for the best.

The connection I made was done without any additional software. I loaded up the live CD and it automatically worked.  Try using the CD and see if what I detailed works straight off.  If this works as I expect then I would suggest that you either re-load 9.10 or wait until the end of the month when 10.04 will be issued.  I would anticipate that 10.04 will work straight out of the box for wireless.

Hope this assists you

---

### Post by no_ordinary_funace on 2010-04-14
Yeah I am working with 9.10 and I got the same instructions as you gave when I read the help section.

> Assuming that you are working with 9.10 you should see next to the sound icon four bars rising from left to right. If you right click on them you should see Enable Networking and Enable Wireless. Ensure that these are both ticked.


There are no bars.  I only see the antenna with 4 dots, which is where I assume these far bars SHOULD be extending from.  I've still got windows installed on a separate partition and I've checked both in areas where there is wireless networking, whether secured or unsecured.  In widows the networks are detected, but in ubuntu nothing.

Right clicking shows an option for ONLY "enable networking" (which is ticked) but NOT for "enable wireless".  The other options in this box are "connection information" which is not clickable and "edit connections..." which is clickable.

When clicking on the "edit connections" button, it takes me to a box with the options "wired", "wireless", "mobil broadband", "vpn", and "dsl".

The "wireless" section is empty.  Is it likely that I need to manually make some kind of adjustment or addition to this box pointing to the built-in wireless card?  The options for this are "name" and "add".

Anyway, I'll try the cd and see what happens.

Thanks.

---

### Post by marshag63 on 2010-04-14
First thing we need to know is what kind of wireless adapter you have so we can determine what driver you should be using.  In a terminal type "lspci" (without quotes).  This will identify your wifi adapter and also give an ID code with a combination of numbers/letters with a colon in the middle.  Once we know this, we can direct you to the correct driver.

MarshaG.

---

### Post by no_ordinary_funace on 2010-04-15
Hi Marsha,

Thanks for your response.

Lesse...I read "the guide" which gives a listing of information which is helpful to post.  It actually looks really long to me, but but for the sake of posterior I'll post it anyway.

Thanks.



It's listed in the same order that the guide lists the suggestions.

=======================================================

potato@potato-laptop:~$ rfkill list

2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

[I dunno why bluetooth is the only option listed here. I tried soft blocking it to see if that would free up the other options but no effect]
========================================================

potato@potato-laptop:~$ lspci

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe


=====================================================

potato@potato-laptop:~$ lsusb

Bus 001 Device 004: ID 0408:13e2 Quanta Computer, Inc. 
Bus 001 Device 002: ID 054c:0243 Sony Corp. MicroVault Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:219b Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


=====================================================

$ lspci -nn | grep 'Wireless Brand'

[This command produces no result whatsoever except to put me back to the command line prompt]

====================================================

potato@potato-laptop:~$ lsmod

Module                  Size  Used by
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat
binfmt_misc             8356  1 
bridge                 47952  0 
stp                     2272  1 bridge
bnep                   12060  2 
ppdev                   6688  0 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
iptable_filter          3100  0 
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
ip_tables              11692  1 iptable_filter
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
joydev                 10272  0 
x_tables               16544  1 ip_tables
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
uvcvideo               59080  0 
videodev               36736  1 uvcvideo
v4l1_compat            14496  2 uvcvideo,videodev
lp                      8964  0 
psmouse                56180  0 
parport                35340  2 ppdev,lp
serio_raw               5280  0 
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
btusb                  11856  2 
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
i915                  221064  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
usb_storage            52544  1 
r8169                  32064  0 
mii                     5212  1 r8169
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video

==============================================================

$ lsmod | grep "wlan_module_name"

[NO EFFECT: this just puts me back to the command line prompt again]

=============================================================

$ dmesg

I skipped this one because it was really, really, really long and I didn't know which parts were the most relevant.  If you still want to see it I can post it.

==========================================================

potato@potato-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:26:9e:a7:ad:79
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:27 ioport:3000(size=256) memory:90010000-90010fff(prefetchable) memory:90000000-9000ffff(prefetchable) memory:90020000-9002ffff(prefetchable)

  *-network UNCLAIMED
       description: Network controller
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:94000000-9400ffff

[I notice that my wireless 802 is listed as unclaimed.  Is that the same thing as not having a driver installed?]

=================================================================

potato@potato-laptop:~$ iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

================================================================

potato@potato-laptop:~$ iwlist scan wlan0

iwlist: unknown command `wlan0' (check 'iwlist --help').

================================================================

potato@potato-laptop:~$ lsb_release -d

Description:    Ubuntu 9.10

===========================================================

potato@potato-laptop:~$ uname -mr

2.6.31-14-generic i686

===========================================================

potato@potato-laptop:~$ sudo /etc/init.d/networking restart

 * Reconfiguring network interfaces...                                   [ OK ]

===========================================================

---

### Post by zerkig on 2010-04-15
This might be helpful although it depends how confident you are with Ubuntu

[http://ubuntuforums.org/showthread.php?t=1313132](http://ubuntuforums.org/showthread.php?t=1313132)

basically the wireless card you've got does not work out of the box with the Karmic kernel. One solution given in the link is to apply some patches. Another is to beg/borrow or steal a usb wireless adapter that does work.

Check the** Networking & Wireless** forum for more.

---

### Post by no_ordinary_funace on 2010-04-16
WAAAAHHHHHHH:(

That looks HAAAARD!  But I downloaded a bunch of pages about updating the kernel and I'll give it a go in the morning.  I once replaced a cracked radiator on an old dodge with very little previous  experience. How hard can this be?

BTW, the patches from [http://www.kernel.org/pub/linux/kern...ing/2.6/2.6.31]("http://www.kernel.org/pub/linux/kernel/people/gregkh/staging/2.6/2.6.31") appear to be set up in such a way that one MUST recompile the kernel manually (or whatever it's called) by cutting and pasting the code into the appropriate places as opposed to click-able programs which do it automatically.  Is that your understanding as well?

Will let you know how it goes.  Thanks for the links.

---

### Post by no_ordinary_funace on 2010-04-21
Okay so I'm back; finally broke down and decided to ask for help.

I found what looks like the correct patch/driver to get my wireless working but I'm having some trouble installing it.

The file is called "rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb"

I found it from another page on these forums.  The address is [https://launchpad.net/~markus-tisoft/+archive/rt3090/+build/1098170]("https://launchpad.net/%7Emarkus-tisoft/+archive/rt3090/+build/1098170")

I think part of the problem is that I don't have ANY  internet connection to my netbook.  I'm doing this stuff from cyber cafes and transferring the files using a flash drive.  When clicking on the downloaded packagage I get an error saying that some of the files could not be downloaded.  

The error lists three files which I found on the web and downloaded buy following the addresses as they were listed.

I was able to add these three files to my synaptic package manager but the main .deb file cannot be added for some reason which I do not know.  It was there with the other three files when I clicked on the "add downloaded packages" in the file menu, but when I do a check for it in the listing it's not there.

I tried dragging and dropping, too.  I also tried some command lines in the terminal but obviously not int he correct way cause I kept getting error messages.

Anyway,  I've done a lot of looking around and now my head is just a big mush of various command lines, websites, and options, options, options...which I can't seem to put together in the correct way.  

Any thoughts would be appreciated.  Thanks.

---

### Post by no_ordinary_funace on 2010-04-22
UPDATE:  Just found some information that suggested I use "GDebi" to open and install the package.  When I tried this it worked and now wireless networks at least appear on my screen, although I've not yet tested if it actually will connect as the networks are password protected.  

Anyway, in the event that anyone else has similar problems, just clicking on the package itself wasn't enough.  I had to open it using GDebi, but I ALSO had to download three dependency packages to make it work, too.  See previous posts for more information about that.

Here is the link to a tutorial on this forum about installing packages which I used.

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

Thanks.

---

