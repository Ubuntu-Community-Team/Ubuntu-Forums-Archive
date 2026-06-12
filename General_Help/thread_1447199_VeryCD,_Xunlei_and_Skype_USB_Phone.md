---
title: "VeryCD, Xunlei and Skype USB Phone"
date: 2010-04-05
forum: General Help
---

### Post by rykel on 2010-04-05
Hi,

I am a heavy Ubuntu user, but recently, I had to use Windows XP to do the following:

[LIST=1]
[*]Install and run VeryCD from [www.verycd.com](www.verycd.com) (this is probably a nice China-customised version of easyMule);
[*]Watch online movies on [www.Xunlei.com](www.Xunlei.com) which requires the installation of a small Xunlei program; and
[*]Use the dialpad on a brandless USB Skype Phone which looks exactly like the one from IPEVO (see attached picture).
[/LIST]
Is there a way I can do all of the above in Ubuntu Lucid, so that I can kiss goodbye to Windows? I am OK with doing things like WINE, Virtualbox etc. too if that is what it takes.

Thank you for your advice!

---

### Post by Hobbes on 2010-04-15
you can use amule to connect to edonkey network which can use any link from verycd.com, search the forums for more info if you need.

you can run xunlei in wine from what I read, but I've never tried it.

No idea about the phone, sorry :)

---

### Post by rykel on 2010-04-19
> **Hobbes said:**
> you can use amule to connect to edonkey network which can use any link from verycd.com, search the forums for more info if you need.

you can run xunlei in wine from what I read, but I've never tried it.

No idea about the phone, sorry :)

In fact, I am the one who updated the amule wiki with instructions on downloading VeryCD! BUT... the truth is, that VeryCD seeds in amule seems to download SLOOOOOOWLY.

As for Xunlei, I have not tried it under WINE, but I guess I will.

I hope some developers pick up on this thread and give us some good news!

---

### Post by ravenong on 2010-06-29
so far i try xunlei run under wine does not success.. keep giving me error message

---

### Post by rykel on 2010-07-01
At this moment, I am forced to run VeryCD easyMule in Crossover. However, it slooooows down my entire PC. Same lacklustre performance as Amule trying to download VeryCD stuff - works, but complicated to set up AND slow.

If you have the computing power, you can run the same software in a virtualised Windows on Ubuntu. This might work too with the movie accelerator program for Xunlei KanKan. Use VMWare instead of Virtualbox as the former is supposed to be way ahead of the latter in 3D rendering.

btw, I wonder why the Chinese have Xunlei KanKan (super-smooth FULL-LENGTH, High Definition [HD] movie streaming) and easyMule (super-easy-to-use emule client) while we have nothing close in the Western/English-speaking world. Please correct me if I am wrong.

(and I have not even started talking about PPLive...)   :lolflag:

---

### Post by rykel on 2011-02-21
Bump. Thanks.

---

### Post by fparri on 2011-04-12
> **rykel said:**
> 
[*]Use the dialpad on a brandless USB Skype Phone which looks exactly like the one from IPEVO (see attached picture).
Got your same phone. Did you resolve your problem? :)

---

### Post by rykel on 2011-04-12
Unfortunately the phone buttons and menus do NOT work on Ubuntu, although it can be used as a speaker and microphone. I have thrown away the phone and no longer uses it with the PC. Anyway, with Android, iPhone and Symbian mobile phones, we can now have a handsfree, cordless Skype phone, so who needs those stinky, Linux-UNfriendly USB phones??    :)

---

### Post by fparri on 2011-04-13
I partly agree. It's true that Skype works with most smartphones on market, but sometimes it's useful to have a USB-powered Skype Phone connected all the time to our PC. Think of office

Pity nobody developed linux-drivers for these devices...

---

### Post by wvu_ravens_fan on 2011-06-06
Install Windows on a Virtual Machine.  I like VirtualBox by Oracle.

---

### Post by linuxinstalledfromhdd on 2011-06-06
> **wvu_ravens_fan said:**
> Install Windows on a Virtual Machine.  I like VirtualBox by Oracle.

You can try Virtualbox 4

```

sudo echo "deb http://download.virtualbox.org/virtualbox/debian $(lsb_release -sc) contrib" | sudo tee /etc/apt/sources.list.d/virtualbox.list
wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install virtualbox-4.0

```

---

### Post by wvu_ravens_fan on 2011-10-15
VeryCD server is available on Amule in the repo.  You will have to port your router.

---

