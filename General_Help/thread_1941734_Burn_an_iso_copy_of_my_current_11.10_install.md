---
title: "Burn an iso copy of my current 11.10 install?"
date: 2012-03-16
forum: General Help
---

### Post by joemartin on 2012-03-16
I know it's possible to do this i just don't know the recommended way.  I want to re-install my current "just the way I have it now" desktop configuration on a laptop.

Thanks.

---

### Post by sudodus on 2012-03-16
I suggest that you get the ***Clonezilla*** iso file, and run Clonezilla live from a CD or USB drive. This way you can make an image of your drive or a partition. It is easy to restore exactly the same system from that image (also using Clonezilla).

If the image is small enough, you can burn it to a DVD disk. Clonezilla uses Partclone, and the image is compressed, so a new installation (without a lot of personal data files) should fit on a DVD disk.

*Edit: If you have no proprietary drivers, the installed system (and clones of it) should work also on other computers. Otherwise you should uninstall those and install the built-in standard driver(s), e.g. for graphics and wifi.*

---

### Post by kazztan0325 on 2012-03-16
There is another way to do it here:
**"How to Make an ISO Copy of Your Hard Drive On Ubuntu"**
[http://www.upubuntu.com/2011/11/how-to-make-iso-copy-of-your-hard-drive.html]("http://www.upubuntu.com/2011/11/how-to-make-iso-copy-of-your-hard-drive.html")

---

### Post by yetiman64 on 2012-03-16
OP, I'm not sure if you want to take a "snapshot" of your current system or create a custom live cd/dvd installer.

For purely backup purposes, dd or clonezilla should be fine.

If you want to create an installer (live cd/dvd) that will install fresh with your added programs, and even your settings, you could look into remastersys as an option. [[COLOR=Blue]--wikipedia info for remastersys--[/COLOR]]("http://en.wikipedia.org/wiki/Remastersys") The link is info only not a download link as I'm not sure of your needs.

Cheers, yetiman64

---

### Post by forrestcupp on 2012-03-16
> **yetiman64 said:**
> 
If you want to create an installer (live cd/dvd) that will install fresh with your added programs, and even your settings, you could look into remastersys as an option. [[COLOR=Blue]--wikipedia info for remastersys--[/COLOR]]("http://en.wikipedia.org/wiki/Remastersys") The link is info only not a download link as I'm not sure of your needs.

Right. The OP doesn't want to make a backup; he wants to reinstall his current setup onto a different computer, his laptop.

[Remastersys](http://www.geekconnection.org/remastersys/index.html) is exactly what you want. It's almost like creating your own Ubuntu-based distro off of what you have currently installed. It will create a live DVD for you, and you can just put it into your laptop and do a fresh installation.

I don't think you'll find a better way to do what you're asking.

---

### Post by Ghost_Mazal on 2012-03-16
+1 for remastersys. I always use it to make redistributable iso's for re-installation on other pc's and laptops.

---

### Post by chickenPie4breakfast on 2012-03-16
I tried remastersys (now uninstalled it) but it just kept complaining that basically I had too much stuff to backup
"The compressed file system is larger than the gen iso-image allows...bla bla"
Even though I havent been using linux long and dont have that much installed.

---

### Post by Ghost_Mazal on 2012-03-16
> **chickenPie4breakfast said:**
> I tried remastersys (now uninstalled it) but it just kept complaining that basically I had too much stuff to backup
"The compressed file system is larger than the gen iso-image allows...bla bla"
Even though I havent been using linux long and dont have that much installed.

You probably chose the "backup" option and have plenty of data in /home.

Use the "distribution" option and just transfer large data in /home via external HDD (if you do need /home transfered)

Also disconnect all mounted mdia (external HDD's or network) before doing remastersys

---

