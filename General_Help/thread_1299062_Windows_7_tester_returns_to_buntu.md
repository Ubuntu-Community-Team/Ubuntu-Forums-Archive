---
title: "Windows 7 tester returns to *buntu?"
date: 2009-10-23
forum: General Help
---

### Post by c_martini on 2009-10-23
I am a web designer / developer and have been a Linux/Windows/Mac user on and off for many years now. This year I was given a company laptop to do what I please with as far as upgrading hardware and installing my o/s and apps of choice...

It is a moderately decent spec machine with a Intel dual core 2ghz cpu, 4gb ram, Ati Mobility Radeon HD 3470 graphics, Realtek HD sound, fingerprint security, face recognition/tracking webcam blah blah etc.

It was shipped preinstalled with Windows Vista which I quickly grew to hate. It is just not meant for portable computers of any kind. Its slow, clunky, heavy and bloated. I stuck with it for awhile as I need a Windows environment day to day for Photoshop (at that time there was no reliable way to run Photoshop Cs3 in Linux under Wine), Dreamweaver and testing of my coding on Windows browsers (Internet Explorer, Firefox, Chrome, Opera, Safari etc). My company has a rather expensive set of licenses for the Adobe Creative Suite so I did not wish to jump ship just then.

I also access a development server for work through webdav. Vista was horrible at managing this and very slow, with various errors from time to time. This is quite a big deal as most of my work day is spent browsing, copying, editing and saving files via this networking method.

In the meantime, Windows 7 public beta was launched in January, and I was told by more than one source that the webdav problems did not exist with Windows 7. Hoping for some improvement in webdav implementation, I jumped into testing Windows 7 x64, and have been doing so, from the beta through release candidate.

Though very impressed with the other improvements in Windows 7 over Vista, The improvement in webdav was only marginal at best. I still suffer with 40-60 second wait times for saving and copying files. I still get errors every so often. 

I do love Windows 7 otherwise but now the end of my trial is approaching and I am taking another hard look at my day to day os needs...

The last Linux distro I used was Kubuntu 8.10 Gutsy Gibbon, so there have been two major releases (if you count upcoming 9.10) since I have been a Linux user. I am considering the follwing debian based distro variants: Ubuntu 9.10, Kubuntu 9.10 & Linux Mint 7 or 8 (when it arrives).

I would like to hear some opinions on typical day to day usage in a work environment from those perhaps in a similar situation.

My main concerns are:


* WEBDAV: I only briefly tried this last year in Kubuntu 8.10. It seemed to work fine, but has anything changed in newer releases?

* WIFI & NETWORKING: Was annoyed with the state of this in previous distros. I now need this working seemlessly on a laptop that usually must jump from wired, to wireless networks at home and in my office.

* ability and ease with which to DUAL BOOT WITH WWINDOWS: I will have to keep Windows for unforeseen testing scenarios. I use Virtualbox to test in earlier browser and windows versions as well.

* MEDIA HANDLING: Most of my previous experience was with Amarok in Kubuntu, which i liked. In Windows, I use Itunes and vlc. Any media players in prospective distros should be compatible with a vast array of portable usb connected players and mobile phones...

* DLNA: My shiny new Samsung lcd tv is internet media and network connected, supporting DLNA. While Windows 7 natively supports this, I found the performance is not so great in my case as many of the video files I typically share on my network are *.mkv contained hd 1080p files, which Windows 7 dlna does not support properly.

Any and all opinions thankfully appreciated! :)

---

### Post by Fire_Chief on 2009-10-23
WebDAV: Not sure as I don't use this but suspect it's probably good.

WIFI/Networking: This will be heavily dependent on the wireless and wired chipsets you have in your laptop. Many many chipsets are working out of the box now but there are still some that don't. Booting up on the Live CD will tell you real quick if it's good.

Dual Booting Windows: Still pretty easy). Check out these how-to's on dual boot setups:
Ubuntu 9.10 with Grub2
[http://ubuntuforums.org/showpost.php?p=8147606&postcount=10]("http://ubuntuforums.org/showpost.php?p=8147606&postcount=10")
Ubuntu 9.04 and earlier with Grub
[http://members.iinet.net/~herman546/]("http://members.iinet.net/~herman546/")
[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")
[http://screencasts.ubuntu.com/2009/09/02/Ubuntu_Dual_Boot_Install]("http://screencasts.ubuntu.com/2009/09/02/Ubuntu_Dual_Boot_Install")

Media handling: VLC is also available in Ubuntu. Amarok can also be used since you are familiar with it. Others prefer Banshee for media device connectivity. Again your mileage may vary depending on the device.

For your DLNA server, I recommend miniDLNA [http://sourceforge.net/projects/minidlna/]("http://sourceforge.net/projects/minidlna/")

Cheers!

---

### Post by c_martini on 2009-10-27
> **Fire_Chief said:**
> WebDAV: Not sure as I don't use this but suspect it's probably good.

I have ended up installing Kubuntu 9.10 rc. While I am unable to establish a webdav connection in Dolphin, It does work well in Konqueror.

> **Fire_Chief said:**
> WIFI/Networking: This will be heavily dependent on the wireless and wired chipsets you have in your laptop. Many many chipsets are working out of the box now but there are still some that don't. Booting up on the Live CD will tell you real quick if it's good.

Karmic recognized the chipsets without a problem. However, I am getting very slow performance from both wired and wireless networking.

Wired: Atheros 'Atheros L1 Gigabit Ethernet 10/100/1000Base-T Controller'

Wireless: 'Intel Wireless WiFi Link 4965AGN'

I will have to do a bit of digging to see if I can resolve this issue.

> **Fire_Chief said:**
> Dual Booting Windows: Still pretty easy). Check out these how-to's on dual boot setups:
Ubuntu 9.10 with Grub2
[http://ubuntuforums.org/showpost.php?p=8147606&postcount=10]("http://ubuntuforums.org/showpost.php?p=8147606&postcount=10")
Ubuntu 9.04 and earlier with Grub
[http://members.iinet.net/~herman546/]("http://members.iinet.net/~herman546/")
[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")
[http://screencasts.ubuntu.com/2009/09/02/Ubuntu_Dual_Boot_Install]("http://screencasts.ubuntu.com/2009/09/02/Ubuntu_Dual_Boot_Install")

This was easy. On install, Kubuntu recognized my Windows 7 install without a problem and added it to the boot menu. I am going to get rid of Win7 as its only a trial version but good to know it can dual boot with this newer operating system nonetheless...

> **Fire_Chief said:**
> Media handling: VLC is also available in Ubuntu. Amarok can also be used since you are familiar with it. Others prefer Banshee for media device connectivity. Again your mileage may vary depending on the device.

Kubuntu comes with Amarok for music. Great app! Also Kaffeine for video, though I usually prefer VLC.

> **Fire_Chief said:**
> For your DLNA server, I recommend miniDLNA [http://sourceforge.net/projects/minidlna/]("http://sourceforge.net/projects/minidlna/")

Thanks for that suggestion as well. I will try this
:D

---

