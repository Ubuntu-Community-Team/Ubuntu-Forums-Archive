---
title: "How To Install Remastersys On Natty?"
date: 2011-06-09
forum: General Help
---

### Post by Chriske on 2011-06-09
Hi,

How would I install Remastersys on Natty 11.04 please?

I tried the instructions from the Remastersys website:

[INDENT][FONT=Courier New][COLOR=Blue]For Karmic, Lucid and Newer with grub2 - version 2.0.13-1 and up[/COLOR][/FONT]
[FONT=Courier New][COLOR=Blue] # Remastersys[/COLOR][/FONT]
[FONT=Courier New][COLOR=Blue]  deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/[/COLOR][/FONT]
[/INDENT]
But, I receive an error message when the software sources reload.

Thank you.

---

### Post by Jose Catre-Vandis on 2011-06-09
Try downloading the deb directly and installing with Gdebi or dpkg:

[http://www.geekconnection.org/remastersys/repository/remastersys/remastersys_2.0.11-1_all.deb](http://www.geekconnection.org/remastersys/repository/remastersys/remastersys_2.0.11-1_all.deb)

```
sudo dpkg -i remastersys_2.0.11-1_all.deb
```

You may have some dependency issues but follow the instructions offered by Gdebi or dpkg if this occurs.

---

### Post by Chriske on 2011-06-09
Thank you very much. That worked fine.

And, it installed directly from the Ubuntu Software Centre. :)

---

### Post by Jose Catre-Vandis on 2011-06-09
> **Chriske said:**
> Thank you very much. That worked fine.

And, it installed directly from the Ubuntu Software Centre. :)


Good news - please mark as solved

---

### Post by Chriske on 2011-06-09
Ah yes!

---

### Post by linuxinstalledfromhdd on 2011-06-09
> **Jose Catre-Vandis said:**
> Try downloading the deb directly and installing with Gdebi or dpkg:

[http://www.geekconnection.org/remastersys/repository/remastersys/remastersys_2.0.11-1_all.deb](http://www.geekconnection.org/remastersys/repository/remastersys/remastersys_2.0.11-1_all.deb)

```
sudo dpkg -i remastersys_2.0.11-1_all.deb
```You may have some dependency issues but follow the instructions offered by Gdebi or dpkg if this occurs.

I've used the deb package to install Remastersys, but sometimes it doesn't create a viable clone of my system or dist option either.  If you want to be sure you have the very latest version, and the additional helper packages to go with it, use this guide instead:

[http://cinderbox.net/2011/06/02/creating-custom-ubuntu-live-usb-with-remastersys/](http://cinderbox.net/2011/06/02/creating-custom-ubuntu-live-usb-with-remastersys/)

---

### Post by Chriske on 2011-06-09
> **linuxinstalledfromhdd said:**
> sometimes it doesn't create...or dist option either.  If you want to be sure you have the very latest version, and the additional helper packages to go with it, use this guide instead:

[http://cinderbox.net/2011/06/02/creating-custom-ubuntu-live-usb-with-remastersys/](http://cinderbox.net/2011/06/02/creating-custom-ubuntu-live-usb-with-remastersys/)


Many thanks for this.

No, it didn't work for me either, so I'm going to try your referred method tomorrow and report back.

---

### Post by cbowman57 on 2011-06-09
> **linuxinstalledfromhdd said:**
> 

[http://cinderbox.net/2011/06/02/creating-custom-ubuntu-live-usb-with-remastersys/](http://cinderbox.net/2011/06/02/creating-custom-ubuntu-live-usb-with-remastersys/)

Giving this a go with a couple changes, going to try adding .local/ and see if it will import my Gnome 3.0 setup.

Thanks for the link. :)

---

### Post by linuxinstalledfromhdd on 2011-06-09
It's always better to use the PPAs or Repositories for Ubuntu software installations, I have found. :)  When you do it just from a direct downloaded deb package, sometimes it doesn't work.  Good luck.:p

---

### Post by Chriske on 2011-06-10
Thanks again.

That method worked for me and I noticed all my personalised applications came across into my custom .iso

I wasn't successful with my desktop, firefox, or other personal settings, so that part of the referred process did not work for me.

But, I think I found another suggestion for that part and I'm going to try that.

And that worked, so I'm now the proud possessor of my own "Chriskebuntu". 

:D

Best wishes

---

### Post by Jose Catre-Vandis on 2011-06-10
I pointed the link to the deb in the ppa so can't see how that might be different?


Remember not to "write / save" your "distro" to ntfs - it won't work properly, always use ext2 - 4.

---

### Post by linuxinstalledfromhdd on 2011-06-10
I think I know what you guys are talking about:

[http://cinderbox.net/2011/06/02/creating-custom-ubuntu-live-usb-with-remastersys/](http://cinderbox.net/2011/06/02/creating-custom-ubuntu-live-usb-with-remastersys/)

---

### Post by Chriske on 2011-06-11
> **Jose Catre-Vandis said:**
> I pointed the link to the deb in the ppa so can't see how that might be different?


Remember not to "write / save" your "distro" to ntfs - it won't work properly, always use ext2 - 4.

Hmmm...I can only say that when I installed with that method and used the app I kept getting a ramdisk error when I tried to boot the new image.

When I tried the same thing following the second method, I didn't.

Maybe I was doing something else wrong? :???:

---

