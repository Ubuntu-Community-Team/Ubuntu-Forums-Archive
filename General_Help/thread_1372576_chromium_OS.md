---
title: "chromium OS"
date: 2010-01-04
forum: General Help
---

### Post by Linux Army on 2010-01-04
Is it possible to install Chromium OS on ubuntu?

---

### Post by meazz1 on 2010-01-04
Yes, follow the instructions.
Change to your what ever release you have.

How to install Chromium on Ubuntu:
(copied from the web)

Open your /etc/apt/sources.list file. 

```
gksudo gedit /etc/apt/sources.list
```

Add these lines at the very bottom of it:

```
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu [COLOR="Red"]VERSION [/COLOR]main
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu [COLOR="Red"]VERSION [/COLOR]main
```
Save and exit.

then upload and install:

```
sudo apt-get update
sudo apt-get install chromium-browser
```

---

### Post by bluestar14 on 2010-01-04
isn't there already google chrome beta for ubuntu?

---

### Post by t0p on 2010-01-04
I think you all need to read the opening post again.  The OP doesn't want to install the Chromium *browser* - he's asking about **Chromium OS** - ie the *operating system*.

**OP:**  ChromiumOS is an operating system.  So you don't install it in Ubuntu, just as you wouldn't install Windows 7 in Ubuntu.

Having said that, you *can* install it as a guest OS in VirtualBox.  I've seen instructions for this, I'll find the link for you.

**EDIT:**  Check out [this thread]("http://ubuntuforums.org/showthread.php?t=1360384"),  there's a link in it to a tutorial I saw on how to make a live usb of ChromeOS.  When you boot ChromeOS from the live usb, there's an option to installl it.  But I believe ChromeOS is optimized to run from a SSD, *not* a conventional hard drive.  But that's just what I read somewhere: check out the instructions for yourself.

---

### Post by Robster2 on 2010-01-04
DO NOT INSTALL CHROMIUM OS STRAIGHT ON YOUR HARDDRIVE AS IT WILL NUKE IT.

The instructions show you how to build run it from a 4GB USB or SUN's Virtual Box like VMWARE but free.

There isos floating about but none of them come from Google and none of them are officially supported.  SO YOU SHOULD BUILD IT YOURSELF it is not hard and the instructions are step by step

You should have Ubuntu 8.10 or higher preferably Karmic 9.10

[http://www.chromium.org/chromium-os/building-chromium-os](http://www.chromium.org/chromium-os/building-chromium-os)

[http://sites.google.com/a/chromium.org/dev/chromium-os/building-chromium-os/build-instructions](http://sites.google.com/a/chromium.org/dev/chromium-os/building-chromium-os/build-instructions).

I think I will give it a run it will give me something to use Virtual Box for.   

:guitar:

---

### Post by shashi859 on 2010-01-21
As far I know you can install it in 2 ways
**1.**running /usr/sbin/chromeos-install ---this will **erase your hard disk completely**
[B]
2.[/B]by copying usb image to hard disk--to know how to do this, just follow wiki available on[ http://chromeos.hexxeh.net/ ]("http://chromeos.hexxeh.net/")

---

### Post by mkvnmtr on 2010-01-21
I ran it for a few days in virtual box. Just mount the iso and boot from it. I never needed to install and just used a small harddrive to attach it . I did not think it was worth keeping so I deleted after a couple of days. It did not seem to nuke my drive either.

---

