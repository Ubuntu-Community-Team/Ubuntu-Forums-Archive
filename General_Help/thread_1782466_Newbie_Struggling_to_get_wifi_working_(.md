---
title: "Newbie Struggling to get wifi working :("
date: 2011-06-14
forum: General Help
---

### Post by wilbur-force on 2011-06-14
Hi. I recently (successfully) installed ubuntu via wubi on my Dell.

I then managed to convince my wife to let me install it on her Samsung N150 - claiming it would speed up her web browsing.

Two days later and i still cant get her wifi to work :(  ive googled loads. I have updated to 10.10 and i have (i think) installed Broadcom drivers. Ive also checked for hardware drivers and its telling me 'no proprietory drivers'.

Can anyone help ? Please be gentle .... ive been tinkering with Linux a bit, and adb to Android, but im way off being classed as an xpert :p

---

### Post by btindie on 2011-06-14
Have you tried this? [URL="http://ubuntuforums.org/showthread.php?t=1635779"]http://ubuntuforums.org/showthread.php?t=1635779
[/URL]

---

### Post by wilbur-force on 2011-06-14
> **btindie said:**
> Have you tried this? [URL="http://ubuntuforums.org/showthread.php?t=1635779"]http://ubuntuforums.org/showthread.php?t=1635779
[/URL]

tried that one. the link doesnt work :(

yours does ... the link in the link doesnt :(

---

### Post by wildmanne39 on 2011-06-14
> **wilbur-force said:**
> Hi. I recently (successfully) installed ubuntu via wubi on my Dell.

I then managed to convince my wife to let me install it on her Samsung N150 - claiming it would speed up her web browsing.

Two days later and i still cant get her wifi to work :(  ive googled loads. I have updated to 10.10 and i have (i think) installed Broadcom drivers. Ive also checked for hardware drivers and its telling me 'no proprietory drivers'.

Can anyone help ? Please be gentle .... ive been tinkering with Linux a bit, and adb to Android, but im way off being classed as an xpert :pHi, run this in a terminal
```
lspci
```
```
sudo lshw -C network
```and post it back here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by wilbur-force on 2011-06-14
```
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
05:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8192E Wireless LAN Controller (rev 01)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller

```

```
PCI (sysfs)
```

does that help ?

---

### Post by wilbur-force on 2011-06-14
oh ... and i now have 'wireless network disconnected' in a constant 'window' top right.

Im very new to this :(

---

### Post by wildmanne39 on 2011-06-14
> **wilbur-force said:**
> ```
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
05:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8192E Wireless LAN Controller (rev 01)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller

```

```
PCI (sysfs)
```

does that help ?
Hi this is a link for the instructions
[http://ubuntuforums.org/showthread.php?t=1239342&highlight=RTL8192E+Wireless&page=9](http://ubuntuforums.org/showthread.php?t=1239342&highlight=RTL8192E+Wireless&page=9)
this is for the driver
[http://www.box.net/shared/v1bpr94j8k](http://www.box.net/shared/v1bpr94j8k)

---

### Post by wilbur-force on 2011-06-14
cheers.

ok ... real noob warning ....

Ive managed to change to the downloads directory (using my old DOS skills)
done the sudo su step

'make' just gave me - make: *** No targets specified and no makefile found. Stop.

---

### Post by wilbur-force on 2011-06-14
or should i have downloaded the driver to a specific driver directory ???

---

### Post by wildmanne39 on 2011-06-14
> **wilbur-force said:**
> or should i have downloaded the driver to a specific driver directory ???Hi, when you download it you needed to extract it with archive manager, the to do the rest of the make you need to change into the directory where you extracted it, with the cd command in the terminal. If you did not extract it and you download it with firefox open firefox, tools,downloads and you should see it then right click on it and choose to open it with archive manager. Then follow the instructions on the page,pay attention to where you extract it to, you will have to put that location into the terminal. those instructions are to be used in a terminal.

---

### Post by btindie on 2011-06-15
Looks like they've changed the format of the posts. the link it should have pointed to is [http://www.kickenhardware.net/showthread.php?19337-Fix-for-wireless-on-Samsung-N150-netbook](http://www.kickenhardware.net/showthread.php?19337-Fix-for-wireless-on-Samsung-N150-netbook) but then again the git URL it mentions no longer exists. I don't know if it's been merged into the main kernel-firmware tree - [git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git](git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git)

I've downloaded the files in the RTL8192E directory and did an md5sum compare against the ones installed on my system (Ubuntu 10.10) and they were identical so I don't know if the above post will help you or not.

Do you have 3 files (boot.img, data.img, main.img) in /lib/firmware/RTL8192E/ ?

Also came across this post which may be worth a try [http://ubuntuforums.org/showthread.php?t=1460038]("http://ubuntuforums.org/showthread.php?t=1460038&page=3") The firmware *.img files in rtl8192e_linux_2.6.0014.0401.2010.tar.gz are again the identical to the ones already installed on my system.

---

### Post by wilbur-force on 2011-06-16
> **wildmanne39 said:**
> Hi, when you download it you needed to extract it with archive manager, the to do the rest of the make you need to change into the directory where you extracted it, with the cd command in the terminal. If you did not extract it and you download it with firefox open firefox, tools,downloads and you should see it then right click on it and choose to open it with archive manager. Then follow the instructions on the page,pay attention to where you extract it to, you will have to put that location into the terminal. those instructions are to be used in a terminal.

sorry - been away.

just followed your instructions and we now have wifi :)

you, sir, are a true gentleman !   :)

---

