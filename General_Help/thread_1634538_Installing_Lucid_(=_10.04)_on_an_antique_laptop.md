---
title: "Installing Lucid (= 10.04) on an antique laptop"
date: 2010-11-30
forum: General Help
---

### Post by Meneer Jansen on 2010-11-30
This topic is to help others and for my own reference. Ubuntu 10.04 long term support (LTS) 10.04 'The Lucid Lynx' with LXDE as it desktop manager (i.e. Lubuntu) is so leightweight that it runs quite well on my antique Toshiba latop! Even google-chromium. Now aint that good news? I'm completely up-to-date w/ the latest stable software completely virus free and w/ suppport for all kinds of modern day applications on an 10+ year old happy lappy!

**My old laptop specs**
Toshiba Tecra 8000 (see picture)
[IMG]http://www.batbelt.org/bilder/tecra8000.jpg[/IMG]
Year: 1999 (pre-Millennium!)
Processor: Pentium II mobile 366 MHz
Memory: 119 MB
Screen: 14", 1024x768, 16 bit/pixels (yes, it was a nice one for its time)
Sound chip: Yamaha OPL3sa2 (supported by Alsa driver snd-opl3sa2)
Harddrive: 6 GB (which I divided in 2).
Network card: pcmcia wireless Orinoco Silver/Gold card.


**Installation process**
Download Ubuntu 10.04 net-install CD and install from internet w/ a plug and play Ethernet pcmcia card. During the installation process choose for Xubuntu (and install lxde later) or Lubuntu. After installation it's important to prevent Ubuntu from autostarting all kinds of processor- and harddrive time consuming actions. Therefore make the files in */etc/cron/daily/* not-executable. Additionally one my deinstall some daemons and software you do not use anyway like: cups (printing), apparmour, gdm (use lxdm instead!), pulseaudio.


**Some tips and hints:**
[LIST]
[*]**ACPI:** the battery monitor and shutting down does not work because acpi (powermanagement) is not enabled in the kernel during boot time. This appears to be because 'Buntu hinks the BIOS of the Tecra is too old. Force 'Buntu to load acpi support by editing the file /etc/default/grub. Add the following to the parameter called 'GRUB_CMDLINE_LINUX':
```

GRUB_CMDLINE_LINUX="acpi=force pci-noacpi"

```
Don't forget to run the following command every time you change the /etc/default/grub file:
```

sudo update-grub

```
[*]**Sensors:** install it w/ the command: "sudo sensors-detect".
[*]**LyX/LaTeX:** runs just fine. Simply instal it with "sudo apt-get install lyx" and wait for a long, long time for the download and install process to finish. ;)
[*]**Tint2 taskbar:** nice looking, leightweight, little taskbar. Configure it by editing the file: "~/.config/tint2/tint2rc".
[*]**Autostart apps:** edit the file: "/etc/xdg/lxsessions/LXDE/atostart".
[*]**Grub2's background:** find a nice jpeg picture and paste it's location in the file: "/etc/grub.d/05_debian_theme" as the variable called "wallpaper" (in line 10) like so:
```

.
.
.
WALLPAPER="/usr/share/images/grub/Windbushencom.tga"

```
Don't forget to run "sudo update-grub" afterwards!
[*]**Lxde's background:** edit the file: "/etc/lxdm/lxdm.conf" and don't forget to run "sudo update-alternatives --config lxdm.conf" afterwards!
[*]**Shortcut keys config:** you need to edit Openbox's preferences (= the windowmanager) for this. It's the file: "~/.config/openbox/lxde-rc.xml".
[*]**gam_server (gamin):** sometimes grabs too much cpu % when Thunar (the file manager) is started. Edit the file: "/etc/gamin/gaminrc" and add the line (if you're using ext2 like):
```

fsset ext2 poll 60

```
[/LIST]

**Getting Orinoco wireless to work:** uninstall wpa_supplicant and its dependencies and configure like, for example, so:
```

sudo iwconfig eth1 key <<your wep key>> essid <<your netw./router name>> rate 11M
sudo dhclient

```

You won't have to be ashamed of that antique lappy anymore :). Look:
[[IMG]http://img18.imageshack.us/img18/285/screenshotgqk.th.png[/IMG]](http://img18.imageshack.us/i/screenshotgqk.png/)

---

### Post by jontheid on 2010-12-01
Truly excellent work!
Any chance of some screenshots just to see what can be done?
I was thinking of trying to use LXDE but opted for straight Xubuntu in the end.
Jon

---

### Post by jontheid on 2010-12-01
What an idiot I am, there's a screenshot at the bottom of thepost.
Looks very swish.

---

### Post by Meneer Jansen on 2010-12-03
> **jontheid said:**
> What an idiot I am, there's a screenshot at the bottom of thepost.
Looks very swish.
If you want some more screens of the theme I'll post them :) But I didn't change much. Just downloaded a slightly altered Openbox window decorator theme. Ain't Linux great? The latest version of XFDE was too much for the humble Pentium II Mobile. LXDE is perfect.

---

