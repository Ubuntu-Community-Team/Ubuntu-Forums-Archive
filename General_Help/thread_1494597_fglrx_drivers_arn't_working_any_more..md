---
title: "fglrx drivers arn't working any more."
date: 2010-05-27
forum: General Help
---

### Post by BlackDex on 2010-05-27
Hello there,

I uninstalled the fglrx drivers to try and get my HDMI output to work.
When i reinstalled the driver, i can't start aticonfig or the control center anymore.

When downloading the v10.5 .run package, and building the deb packages, i also see that they are on the wrong location.

When i download the v10.4 .run package, it seems to be on the correct location.

Trying to install it using the Hardware Drivers (jockey), also gives the wrong location. Installing using Synaptic has the same result.

I have tried "https://help.ubuntu.com/community/BinaryDriverHowto/ATI"
and "https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver"

But nothing seems to work.

What am i doing wrong?
How can i fix this, or force the files to be in the correct folder?

Thx in advance.

---

### Post by alphacrucis2 on 2010-05-27
> **BlackDex said:**
> Hello there,

I uninstalled the fglrx drivers to try and get my HDMI output to work.
When i reinstalled the driver, i can't start aticonfig or the control center anymore.

When downloading the v10.5 .run package, and building the deb packages, i also see that they are on the wrong location.

When i download the v10.4 .run package, it seems to be on the correct location.

Trying to install it using the Hardware Drivers (jockey), also gives the wrong location. Installing using Synaptic has the same result.

I have tried "https://help.ubuntu.com/community/BinaryDriverHowto/ATI"
and "https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver"

But nothing seems to work.

What am i doing wrong?
How can i fix this, or force the files to be in the correct folder?

Thx in advance.

I just installed Catalyst 10.5 on Lucid 64 and it worked ok. 

To install 10.4 just use the one in the Ubuntu repos via System - Administration - Hardware drivers. For 10.5 which was only just released by AMD, get the installer from the AMD/ATI website and follow their instructions. At the end I found that I had to do:

```
sudo aticonfig --initial -f
```

The AMD instructions don't mention the -f but I found that without that, aticonfig was complaining about screens. The Catalyst 10.5 seems to be a marked improvement for me with a HD 3400. Desktop effects enabled and full screen video's, opengl apps like googleearth and stellarium all running well. I also have the Xorg backclear patch installed which is essential for window restores to get good performance with Catalyst.

Edit: Sorry - I missed the bit where you said you had tried installing via Jocky. Which version of Ubuntu are you running?

---

### Post by BlackDex on 2010-05-27
Well, i get the message "aticonfig: command not found"

if i look for the command it was somewhere in /usr/lib/fglrx/bin/aticonfig

If i then try to start that command, i get the error that /etc/ati/control is not found.

When i look for that file, it is also at the wrong place.
I realy, realy am puzzled about this error.

---

### Post by alphacrucis2 on 2010-05-27
> **BlackDex said:**
> Well, i get the message "aticonfig: command not found"

if i look for the command it was somewhere in /usr/lib/fglrx/bin/aticonfig

If i then try to start that command, i get the error that /etc/ati/control is not found.

When i look for that file, it is also at the wrong place.
I realy, realy am puzzled about this error.

Odd. On my machine aticonfig is in /usr/bin. You didn't try an installer intended for another distro by any chance?

Found this:

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/569871]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/569871")

Sounded a bit similar

---

### Post by BlackDex on 2010-05-28
Ahhhh.... Thx..
I got it to work via that bug report.
A pitty i still can't switch the GPU, but o well, i atleast have the drivers working.

I did the following (located here [https://wiki.ubuntu.com/X/Drivers):](https://wiki.ubuntu.com/X/Drivers):)

```

How to install the fglrx driver manually if Jockey doesn't work for you

(please file bug reports against Jockey if you experience problems with it) 

1) Make sure that the kernel headers for your kernel are installed 

sudo apt-get install linux-headers-$(uname -r) 

2) Install the fglrx driver: 

sudo apt-get install fglrx 

3) Select the driver that you wish to use (fglrx in this case): 

sudo update-alternatives --config gl_conf
sudo ldconfig
sudo update-initramfs -u

4) Configure your xorg.conf 

sudo aticonfig --initial 

5) Restart your computer (restarting only the xserver might not work) 

Note: if you wish to see what alternative is in use (i.e. what driver is installed and enabled) you can use the following command: sudo update-alternatives --display gl_conf

```

---

### Post by osarusan on 2010-08-30
Thanks for posting this!

> 3) Select the driver that you wish to use (fglrx in this case): 

sudo update-alternatives --config gl_conf
sudo ldconfig
sudo update-initramfs -u

This line saved me so much stress! It was stuck on manual mode and I was finally able to change it back to auto mode. Thank you so much for pointing this out!

---

