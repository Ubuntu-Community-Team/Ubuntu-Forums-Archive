---
title: "How do you know how much space is an app?"
date: 2012-07-06
forum: General Help
---

### Post by AbhiKap on 2012-07-06
Hello, 

I have Ubuntu 12.04 on my lapto in duel boot with Windows 7. I would like to know how you can find out how many megabytes or how much space are certain apps from The Ubuntu Software Center. It doesn't say that when I click more info. 

Thanks, Help is appreciated.

---

### Post by drs305 on 2012-07-06
On my system, In the Software Center, if you find the app by typing it in the search box, highlight the package, and then click the "More info" it will display the total size on disk. If it's not installed, it will display how much it will download and what the final size will be.

Do you get any info?

If not, try checking in Synaptic (Properties).

---

### Post by wojox on 2012-07-06
```
wojox@wojox-laptop:~$ apt-cache show gnome-terminal
Package: gnome-terminal
Status: install ok installed
Priority: optional
Section: gnome
Installed-Size: 729
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Architecture: amd64
Version: 3.4.1.1-0ubuntu1
Replaces: gnome-terminal-data (<< 2.26.2-3)
Provides: x-terminal-emulator
Depends: gconf-service, libatk1.0-0 (>= 1.12.4), libc6 (>= 2.4), libgconf-2-4 (>= 2.31.1), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.31.8), libgtk-3-0 (>= 3.3.6), libice6 (>= 1:1.0.0), liblaunchpad-integration-3.0-1 (>= 0.1.17), libpango1.0-0 (>= 1.14.0), libsm6, libvte-2.90-9 (>= 1:0.30.1-2ubuntu1), libx11-6, gsettings-desktop-schemas (>= 0.1.0), gnome-terminal-data (>= 3.4), gnome-terminal-data (<< 3.5)
Recommends: yelp, gvfs
Description: GNOME terminal emulator application
 GNOME Terminal is a terminal emulation application that you can use to
 perform the following actions:
  - Access a UNIX shell in the GNOME environment.
  - Run any application that is designed to run on VT102, VT220, and xterm
 terminals.
 .
 GNOME Terminal features the ability to use multiple terminals in a single
 window (tabs) and profiles support.
Original-Maintainer: Guilherme de S. Pastore <gpastore@debian.org>

```

---

### Post by sudodus on 2012-07-06
In Synaptic, just before confirming to install 'Applying the following changes' you will get a summary with

- number of packages
- extra space used after installation (what you ask for)
- download size

See the attached file

---

### Post by AbhiKap on 2012-07-07
Thanks everyone for the information. Also, how can you know how much space you have left on your computer? I installed Ubuntu alongside Windows 7 with Wubi and I have it 6 GB. How do I know how much of that space is left? Thanks. Help is appreciated.

---

### Post by sudodus on 2012-07-07
You mean how much is left for Ubuntu?

When booted into Ubuntu you can run the terminal command ```
df
``` If you want help to interpret the result, please post the output in a new reply! Wrap code tags around the output text (click on the # sign at the top of the editing window).

In principle, the space left in the root partition "/", is what is available now for Ubuntu.

And if you want, we can also check how much space there is in the other partitions, and how your system can be reconfigured to allow more space for Ubuntu. In that case, run the following command in Ubuntu ```
sudo fdisk -lu
``` Furthermore, please boot Windows and run the disk management tool

[[COLOR="Red"]_http://pcsupport.about.com/od/termsd/p/disk-management.htm_[/COLOR]]("http://pcsupport.about.com/od/termsd/p/disk-management.htm")

where you can see each partition in Windows, its size and free space.

---

