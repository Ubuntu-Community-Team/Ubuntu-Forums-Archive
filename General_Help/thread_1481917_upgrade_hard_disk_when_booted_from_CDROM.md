---
title: "upgrade hard disk when booted from CDROM?"
date: 2010-05-13
forum: General Help
---

### Post by tunahead on 2010-05-13
[SIZE=2]Hi, here is the short version:
How do I upgrade [/SIZE][SIZE=2]Karmic Koala [/SIZE][SIZE=2]9.10 [/SIZE][SIZE=2]on hard disk to Lucid Lynx 10.04 LTS when booted from CDROM?

Long version:[/SIZE][SIZE=2]
I have been running Karmic Koala [/SIZE][SIZE=2]9.10 [/SIZE][SIZE=2]and tried to upgrade to Lucid Lynx 10.04 LTS using the Update Manager.  Partway through I got a message saying I had insufficient space in /  .       I deleted old logs, etc. but still needed more space freed up.

I removed a bunch of packages and trashed the system.  It boots, but no gnome or KDE found.  I have booted from an old (6.06 Dapper Duck) CDROM and when I run [/SIZE][SIZE=2]the Update Manager, it of course sees the running OS on the CDROM rather than the hard disk.  [/SIZE][SIZE=2]How do I upgrade [/SIZE][SIZE=2]Karmic Koala [/SIZE][SIZE=2]9.10 [/SIZE][SIZE=2]on hard disk to Lucid Lynx 10.04 LTS when booted from CDROM?  Thanks
[/SIZE]

---

### Post by ryan858 on 2010-05-13
I actually had a similar problem going from Jaunty to Lucid... Basically what I did was to download the Lucid ISO using my Januty CD and then burn the ISO using CD/DVD Creator in Applications>Accessories.

Even if you don't have CD/DVD Creator, you can use apt or Synaptic to install it, or install a different burning tool if you like, even download it from the web using Firefox, if all else fails.

---

### Post by jocko on 2010-05-13
You'll have to chroot into the hard disk install.
[This post]("http://ubuntuforums.org/showpost.php?p=8576910&postcount=4") should get you started. Once you have set up and started the chroot environment (i.e after the "sudo chroot ..." command in the linked post), you can probably start the upgrade by typing the command "update-manager" from within the chroot.

---

