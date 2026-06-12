---
title: "How to install applications manually"
date: 2011-01-18
forum: General Help
---

### Post by asifnaz on 2011-01-18
have an old laptop its Pentium III with 384 mb ram and20gb HD . I want to put Ubuntu 10.04 on it . The problem is that it does not has a Ethernet card so I can not go online with it . It has one USB port though .

I want to download .deb files from ([http://packages.ubuntu.com/](http://packages.ubuntu.com/) ) and using my other PC and put them on usb stick and copy to that laptop and dpkg -i .

the problem is that I am a new user so I am confused how to do that as I can mishandle dependencies ( don't know how many required to get one app work and where to get all of them to run an app like vlc , Frozen Bubble etc ) 

For example if you were to manually install VLC in that laptop how would you do that ...???

I am relatively new user and will appreciate your help .

thank you

---

### Post by sisco311 on 2011-01-18
Try keyrix:
[http://keryxproject.org/](http://keryxproject.org/)

---

### Post by lithopsian on 2011-01-18
Ubuntu may not be the best distro for your laptop, might be a bit slow.  Do you have a CD?  Very easy to install from a CD.  Are you sure it can be booted from a USB stick?

Anyway, "installing" an application is not some arcane hidden process like Windows,  In most cases, it is as simple as unpacking a tarball or zip archive into a folder and executing the program.  Ideally, there are some configuration files and perhaps a startup daemon that you'd also like, and these files are automatically installed from a package by the update manager.  You can do the same thing manually.

Ubuntu is fairly complete with applications, and I'm 99% sure that vlc is on there by default.

Keeping your applications up to date without an internet connection is tricky, but also not really necessary.  It is always possible in individual cases to download a deb file using another machine, copy it across, and then install it just as if you were using the update manager through the internet.

---

### Post by smurphy_it on 2011-01-18
Yeah not sure I'd be using ubuntu on older hardware like that.  Did you try any of the light disto's like puppylinux or DSL (Damn Small Linux) ?

If you weren't using the 1 USB port, you could always get a wifi connection via USB key.. alternatively, get a USB hub + usb wifi... Might take a little bit of configuring to get it going, but could get you online.
{food for thought}

---

### Post by lithopsian on 2011-01-18
Of course if you already had Ubuntu on there, you could just plug in a USB dongle, type in your router password, and be on the internet in seconds ;)

Recent versions of Windows are pretty much the same, but they wouldn't even run on that laptop.  Older versions can be a nightmare to set up with wireless and I wouldn't even bother trying.

---

### Post by asifnaz on 2011-01-19
> **lithopsian said:**
> Ubuntu may not be the best distro for your laptop, might be a bit slow.  Do you have a CD?  Very easy to install from a CD.  Are you sure it can be booted from a USB stick?

Anyway, "installing" an application is not some arcane hidden process like Windows,  In most cases, it is as simple as unpacking a tarball or zip archive into a folder and executing the program.  Ideally, there are some configuration files and perhaps a startup daemon that you'd also like, and these files are automatically installed from a package by the update manager.  You can do the same thing manually.

Ubuntu is fairly complete with applications, and I'm 99% sure that vlc is on there by default.

Keeping your applications up to date without an internet connection is tricky, but also not really necessary.  It is always possible in individual cases to download a deb file using another machine, copy it across, and then install it just as if you were using the update manager through the internet.

I will look for a light distro like Xubuntu or Debian 5 . VLC is not default on any distro IMO . I don't need to install updated apps anyway .

My question was how to install app+dependencies . Most of the cases a single deb file may not work if we dont install depencies .

And for other user dongle is expensive than laptop it self .

And don't underestimate the hardware I mentioned . It can run Ubuntu 10.4 fairly well ( If I dont install bloated apps and games )

---

### Post by mastablasta on 2011-01-19
because of PIII i would suggest Lubuntu or Slitaz. they need much less RAM and also are lighter on the CPU. Debian 5 might also be an option (as it uses much less ram), though the applications there could be a bit older.

---

### Post by veggen on 2011-01-19
I'd really suggest you listen to sisco311 and go with keyrix. It's made to do exactly what you're looking for.

---

### Post by veggen on 2011-01-19
<deleted. accidental double post due to this forum's retardations>

---

### Post by asifnaz on 2011-01-19
> **sisco311 said:**
> Try keyrix:
[http://keryxproject.org/](http://keryxproject.org/)

I will look over it .

---

