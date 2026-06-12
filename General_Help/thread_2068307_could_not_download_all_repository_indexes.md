---
title: "could not download all repository indexes"
date: 2012-10-08
forum: General Help
---

### Post by daemon77 on 2012-10-08
i ahve just got a pc with linux ubuntu 7.04. i am quite new to linux, when i try to install anything or updates i keep getting cannot download all repository indexes.
i typed sudo apt-get update in terminal and this is what i got:

fred@fred-desktop:~$ sudo apt-get update
Password:
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
  404 Not Found [IP: 91.189.92.189 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
  404 Not Found [IP: 91.189.92.189 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
  404 Not Found [IP: 91.189.92.189 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
  404 Not Found [IP: 91.189.92.189 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages
  404 Not Found [IP: 91.189.92.189 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages
  404 Not Found [IP: 91.189.92.189 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.189 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.189 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.189 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.189 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.189 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.189 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
fred@fred-desktop:~$ 

tried updating ubuntu and get the same, could not download all repository indexs.
if anyone could offer a solution, it would be much appreciated.

thanks

---

### Post by jerrrys on 2012-10-08
Hi daemon77, welcome to the forums  :)

7o4 reached its end of life back in 2008.  We are running 12.04 these days.

---

### Post by daemon77 on 2012-10-09
> **jerrrys said:**
> Hi daemon77, welcome to the forums  :)

7o4 reached its end of life back in 2008.  We are running 12.04 these days.

So wot do I have to do update the ubuntu. I have downloaded the latest (12.04) how do/ wot do I need to do yo install it?
the latest version i have downloaded is an iso file do i have to extract this, i have read that i can install from a usb or disk, i have both. do i need to format the system or can i install it over 7o4. sorry for the newbie questions but like i said i am new to linux.

---

### Post by stinkeye on 2012-10-09
> **daemon77 said:**
> So wot do I have to do update the ubuntu. I have downloaded the latest (12.04) how do/ wot do I need to do yo install it?
the latest version i have downloaded is an iso file do i have to extract this, i have read that i can install from a usb or disk, i have both. do i need to format the system or can i install it over 7o4. sorry for the newbie questions but like i said i am new to linux.

Instructions for making bootable CD"s or usb stick in  either windows or ubuntu are on the download page.
After making the bootable CD or usb stick boot up with the usb or cd inserted. You need to choose CD or usb as your first boot device in the BIOS.
You will boot into a live session where nothing is installed on your system.
Click the try button to continue the live session to see how it works on your system.
[**_[COLOR="DarkRed"]http://www.ubuntu.com/download/desktop[/COLOR]_**]("http://www.ubuntu.com/download/desktop")

---

### Post by daemon77 on 2012-10-09
> **stinkeye said:**
> Instructions for making bootable CD"s or usb stick in  either windows or ubuntu are on the download page.
After making the bootable CD or usb stick boot up with the usb or cd inserted. You need to choose CD or usb as your first boot device in the BIOS.
You will boot into a live session where nothing is installed on your system.
Click the try button to continue the live session to see how it works on your system.
[**_[COLOR="DarkRed"]http://www.ubuntu.com/download/desktop[/COLOR]_**]("http://www.ubuntu.com/download/desktop")

Thanks

---

### Post by Lyfang on 2012-10-09
Backup and copy over all of your personal files before you install Ubuntu. Maybe Linux Mint is more user-friendly, well at least according some users. Linux Mint 13 with codecs (or without) is based on upstream Ubuntu 12.04, Linux kernel 3.2, the desktop environment MATE 1.2 or Cinnamon 1.4.

---

### Post by cortman on 2012-10-09
> **Lyfang said:**
> Backup and copy over all of your personal files before you install Ubuntu. Maybe Linux Mint is more user-friendly, well at least according some users. Linux Mint 13 with codecs (or without) is based on upstream Ubuntu 12.04, Linux kernel 3.2, the desktop environment MATE 1.2 or Cinnamon 1.4.

If their computer was running 7.04, that indicates that it'd be about too old for Linux Mint; at least IMO.
To the OP; you haven't given us any specs on your machine but if it is fairly old you'd probably be better of running [Xubuntu]("http://xubuntu.org/") or [Lubuntu]("http://lubuntu.net/"), which is Ubuntu with a more lightweight desktop environment.

---

### Post by jerrrys on 2012-10-09
Good point cortman.  X or Lubuntu may be a better choice, depends on your puter specs.

---

### Post by daemon77 on 2012-10-13
cheers guys i am going to user either lubuntu or xubuntu. the computer is about 6 yr old and i will be upgrading all necessary parts to get it up to date, but until then i will go with the light versions. all my computers run windows and this is my first step into linux. i have a sgs3 phone which is open source android, which i believe is linux based, that is as close as i have come to linux.
    is making a bootable usb or disc the same for xubuntu/lubuntu as it is fir ubuntu.

---

### Post by Lyfang on 2012-10-13
> **daemon77 said:**
> all my computers run windows and this is my first step into linux.
[Wubi Windows installer]("http://www.ubuntu.com/download/desktop/windows-installer") is a very easy way to try to install and uninstall *buntu. I would choose Lubuntu. Some consider Wubi to be buggy, since installed on a virtual disk on the NTFS filesystem, which makes it more sensitive. But I'm using Wubi Lubuntu 12.04 without any problems, beyond a fresh normal *buntu installation. You could also choose to wait until the Ubuntu 12.10 Final Release in October 18th. See also: [Wubi Uninstallation]("https://wiki.ubuntu.com/WubiGuide#Uninstallation")

---

