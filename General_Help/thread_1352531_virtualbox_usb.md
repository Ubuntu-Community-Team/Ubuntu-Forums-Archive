---
title: "virtualbox usb"
date: 2009-12-11
forum: General Help
---

### Post by deedz on 2009-12-11
Hello, i just moved from sabayon to ubuntu, but i really need usb for virtualbox I was wondering if anyone can help. I have ubuntu 9.10. If i need the closed source i will get it i dont know how or where though, is there a terminal command i could use i am kind of a newb and only have a basic idea of how to use the terminal. f i get the closed source do i uninstall the old virtualbox? any help is greatly appreciated. I tried the add user but virtualbox wasnt there, when i plug in a usb it doesnt pick anything up it just says no USB devices in gray.

Thanks,
Nick

---

### Post by howefield on 2009-12-11
> **deedz said:**
> If i need the closed source i will get it i dont know how or where though,

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

Download the relevant .deb package for your Ubuntu version and double click the downloaded file to start installation.

> f i get the closed source do i uninstall the old virtualbox?

Yes.

---

### Post by deedz on 2009-12-11
This is the message i get

Error: Conflicts with the installed package 'virtualbox-ose'

---

### Post by mcdjork on 2009-12-11
You have to uninstall Virtualbox OSE before installing Virtualbox. Rather than downloading the deb file, I recommend you add the Virtualbox repository to yours sources list. Read about it here: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads).

With USB devices, printers in particular, I've seen users have problems accessing the devices through virtualbox. They are visible but grayed out. If this happens, you'll have to either run Virtualbox as root (probably a bad idea) or give yourself the correct permissions.

---

### Post by kwstas on 2010-02-02
> or give yourself the correct permissions.     ..so how can i do this?
my vb shows the usb drive in grey...

everything is ok!
i did these here: [https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB)

---

