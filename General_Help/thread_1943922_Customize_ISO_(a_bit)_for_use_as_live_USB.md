---
title: "Customize ISO (a bit) for use as live USB?"
date: 2012-03-20
forum: General Help
---

### Post by littlebigman on 2012-03-20
Hello

I'm looking for a good Linux distro localized for French for use on a USB keydrive for daily use, ie. not as an alternative to a CD to install Linux on the hard disk.

I tried a [localized 11.10](http://ubuntu-fr.org/telechargement) Ubuntu, then used [LinuxLive USB Creator 2.8.11](http://doc.ubuntu-fr.org/live_usb#installation_depuis_windows) to burn the ISO onto a USB keydrive.

It works fine, but I need to change a few items:
[list]
[*]After booting into Ubuntu, a window displays a prompt: "Welcome : Try Ubuntu, Install Ubuntu", which users will find puzzling. Can I remove this prompt?
[*]How to remove the "Install Ubuntu 11.10" shortcut in the upper left-hand corner?
[*]Can I customize the icon bar on the left (Unity?) to get rid of LibreOffice and add a couple of items of my own (Gparted, a Mono-based applet I wrote, etc.)?
[*]Can I mount the USB keydrive to recover files from the hard disk (basic Recovery Disk)?
[/list]

Thank you.

---

### Post by Cheesemill on 2012-03-20
Install and customise Ubuntu however you like and then use Remastersys to create a bootable ISO. You can then use USB Creator to write this onto a USB stick.

[http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)

---

### Post by littlebigman on 2012-03-20
Thanks for the tip. I'll experiment with Remastersys to see if it's a good solution to customize localized editions.

---

### Post by oldfred on 2012-03-20
How large is flash drive. If 8GB or more you can just do a full install.

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

---

### Post by littlebigman on 2012-03-20
Thanks. Initially, I didn't even think of using a persistent key, but a full install might be a good option.

Apparently, Remastersys is deadware: "Remastersys itself has been discontinued. Apparently, there's a new project called [relinux]("http://re-linux.sourceforge.net/") you may want to check out. I haven't tried it myself yet, though." ([source]("http://www.psychocats.net/ubuntu/remastersys"))

Anyway, I couldn't install it after booting Ubuntu: I ran "apt-get update" followed by "apt-get install remastersys", but it says "Package not found".

I'll check Relinux.

---

### Post by Cheesemill on 2012-03-20
Remastersys is alive and well, check their home page:
[http://www.geekconnection.org/remastersys/index.html](http://www.geekconnection.org/remastersys/index.html)

You need to add a repository to install it, instructions are at the bottom of this page:
[http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)

---

### Post by littlebigman on 2012-03-22
Thanks, I'm reading about Remastersys.

Does someone know if I can remove "linux-image-3.0.0-12-generic" from the  running instance before saving it into an ISO, or is it required?

```

root@ubuntu:~# dpigs -n 20
114040 linux-image-3.0.0-12-generic
108920 libreoffice-core
85376 linux-headers-3.0.0-12
45756 smbclient
42820 thunderbird
42576 libreoffice-common
39776 linux-firmware
38116 firefox
25040 libreoffice-help-fr
24832 perl-modules
22648 app-install-data
22520 libreoffice-writer
22072 ubuntu-docs
21824 libwebkitgtk-1.0-0
21820 libwebkitgtk-3.0-0
20300 libc6-dev
19624 humanity-icon-theme
19440 language-pack-gnome-fr-base
18268 samba-common-bin
18268 libicu44

```

---

### Post by Cheesemill on 2012-03-22
I don't think that removing the kernel would be a good idea.

Not if you still want a working system anyway :)

---

### Post by sudodus on 2012-03-22
> **Cheesemill said:**
> I don't think that removing the kernel would be a good idea.

Not if you still want a working system anyway :)
+1

But if you have two such files with different version number, you could have removed the older one. For example, in 10.04 LTS I have
> 97080 linux-image-2.6.32-39-generic
97060 linux-image-2.6.32-38-generic
and I could have removed the older one, but actually, I should have used a more thorough method to remove all files belonging to that older kernel version before running Remastersys.

---

### Post by Megaptera on 2012-03-22
Hi littlebigman,
Have you looked at PearOS? Here: [http://pear-os-linux.fr/](http://pear-os-linux.fr/)

From Distrowatch "Pear OS is a French Ubuntu-based desktop Linux distribution. Some of its features include ease-of-use, custom user interface with a Mac OS X-style dockbar, and out-of-the-box support for many popular multimedia codecs."

Hope this may be of interest to you?

---

### Post by littlebigman on 2012-03-22
I guess I'll leave the kernel files alone, then ;-)

Thanks for the link on PearOS. I did check it out briefly, but didn't like it because it appears to be a very small distro ("[Pear Linux]("http://pear-os-linux.fr/index.php?option=com_content&view=article&id=74&Itemid=24") is a French distribution. It was created by David Tavares, Deux-Sèvres (79), France."); I don't want to invest time mastering the intricacies of a distro only to get stuck at a bug without any help.

At this point, in terms of language + traction + looks, it's pretty much Ubuntu/Mint and Fedora.

---

