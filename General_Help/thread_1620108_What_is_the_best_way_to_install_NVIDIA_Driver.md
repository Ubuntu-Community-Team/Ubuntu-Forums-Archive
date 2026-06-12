---
title: "What is the best way to install NVIDIA Driver?"
date: 2010-11-12
forum: General Help
---

### Post by Aydos on 2010-11-12
I was wondering the best way to install an official NVIDIA driver from [www.nvidia.com](www.nvidia.com) .

I know most people will say to install the additional drivers version that comes with Ubuntu, but I have 2 reasons for wanting the newest nvidia driver.

One reason is I sometimes run my sound out of my monitor over an HDMI cable. With the ubuntu drivers it will not work with my monitor. I have tried it every way and it just wont.

The other reason is I am an avid gamer and I play many Windows based games via WINE and a couple of them require me to run the newest Nvidia drivers to get it to run.

I know a way to do this that I found on the internet, but it is a royal pain and kind of dated. I am hoping there is a better way.

I am doing a reinstall this weekend of Ubuntu 10.10 and I would like to be able to do the Nvidia driver a little more efficiently.

Thank you in advance.

---

### Post by DeMus on 2010-11-12
Go to: [_Nvidia-vdpau_]("https://launchpad.net/~nvidia-vdpau/+archive/ppa"), add the repository to your Synaptic repository list, including the gpg key and install it from within Synaptic.
That way things go automatically plus you will get automatic updates when they appear.

---

### Post by Aydos on 2010-11-12
> **DeMus said:**
> Go to: [_Nvidia-vdpau_]("https://launchpad.net/~nvidia-vdpau/+archive/ppa"), add the repository to your Synaptic repository list, including the gpg key and install it from within Synaptic.
That way things go automatically plus you will get automatic updates when they appear.

Really? That is awesome. And this would be the newest driver just like selecting my 275GTX and my OS?

You might have just made my day.

---

### Post by Aydos on 2010-11-12
Looks like that is a slightly older version of the driver as well.

What steps would I take to manually install the driver downloaded from NVIDIA? I want to be able install and remove the drivers often since I game so much and would like to no the suggested method.

Most of the posts I make or find from searching on this topic always have another option as the answer instead of the method to manually install the drivers.

All ideas are welcome :) That is how I continue to learn, but I really want to know the install method at this point.

Normally I download the driver, save it to my desktop, purge my drivers, edit a file to blacklist drivers, ctrl + alt + F2 to crash to a text menu, stop the video service, cd to my desktop, install the driver, restart the video service.

I am wondering if there is another way to do it from that complicated method that will give me less errors.

---

### Post by Cavsfan on 2010-11-12
> **Aydos said:**
> Looks like that is a slightly older version of the driver as well.

What steps would I take to manually install the driver downloaded from NVIDIA? I want to be able install and remove the drivers often since I game so much and would like to no the suggested method.

Most of the posts I make or find from searching on this topic always have another option as the answer instead of the method to manually install the drivers.

All ideas are welcome :) That is how I continue to learn, but I really want to know the install method at this point.

Normally I download the driver, save it to my desktop, purge my drivers, edit a file to blacklist drivers, ctrl + alt + F2 to crash to a text menu, stop the video service, cd to my desktop, install the driver, restart the video service.

I am wondering if there is another way to do it from that complicated method that will give me less errors.


Go here [[COLOR=blue]_http://www.nvidia.com/Download/index.aspx?lang=en-us_[/COLOR]]("http://www.nvidia.com/Download/index.aspx?lang=en-us") and pick your card.

And here are [[COLOR=blue]_instructions on how to install it._[/COLOR]]("http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html")
It worked well for me.

You really want to print those instructions out at least step 4.

---

### Post by Aydos on 2010-11-12
> **Cavsfan said:**
> Go here [[COLOR=blue]_http://www.nvidia.com/Download/index.aspx?lang=en-us_[/COLOR]]("http://www.nvidia.com/Download/index.aspx?lang=en-us") and pick your card.

And here are [[COLOR=blue]_instructions on how to install it._[/COLOR]]("http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html")
It worked well for me.

You really want to print those instructions out at least step 4.

Ok that is the way I always do it. I was just wondering if it was the most efficient way.

I appreciate the posts I will mark this as solved now.

---

### Post by Cavsfan on 2010-11-12
BTW the Linux driver came out yesterday 260.19.21!
I'm installing it now. :)

---

### Post by Z06Gal on 2010-11-13
> **DeMus said:**
> Go to: [_Nvidia-vdpau_]("https://launchpad.net/~nvidia-vdpau/+archive/ppa"), add the repository to your Synaptic repository list, including the gpg key and install it from within Synaptic.
That way things go automatically plus you will get automatic updates when they appear.


I followed this and got this message:

W: Failed to fetch [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  404  Not Found

---

### Post by SeijiSensei on 2010-11-14
There's [no maverick driver]("http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/dists/") at that PPA.

If, like me but unlike the original poster, you don't feel the need to be using the very latest cutting-edge driver from the Nvidia site itself, just use the "Additional Drivers" application that comes with Ubuntu and let it handle the rest.

---

### Post by Cavsfan on 2010-11-14
> **SeijiSensei said:**
> There's [no maverick driver]("http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/dists/") at that PPA.

If, like me but unlike the original poster, you don't feel the need to be using the very latest cutting-edge driver from the Nvidia site itself, just use the "Additional Drivers" application that comes with Ubuntu and let it handle the rest.

This is good advice. I installed the latest driver nVidia has to offer and it runs a bit hot.
137F (not sure in Celsius) at startup and after bringing up Firefox and waiting a while, it is now at 122F (50C) at 80F room temp.
I can deal with it since I don't do anything graphic intensive with Ubuntu. And there is just a slight noticeable difference between 
this and the default OpenGL driver. I'll probably just leave it.

---

### Post by Cavsfan on 2010-11-14
> **DeMus said:**
> Go to: [_Nvidia-vdpau_]("https://launchpad.net/%7Envidia-vdpau/+archive/ppa"), add the repository to your Synaptic repository list, including the gpg key and install it from within Synaptic.
That way things go automatically plus you will get automatic updates when they appear.

> **Z06Gal said:**
> I followed this and got this message:

W: Failed to fetch [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  404  Not Found


BTW, I went by some of the instructions on my post above as far as blacklisting the files mentioned, but I booted into recovery mode to 
install the driver via these commands:
You have to stop the X server and nVidia suggested I go into telinit 3 mode, so here is what I did.

```
1 - I blacklisted the files mentioned in the file **/etc/modprobe.d/blacklist.conf** 
    per the instructions.
2 - Deleted all nvidia files via **sudo apt-get --purge remove nvidia-*** but there were none 
    to delete as I have done this before.
3 - Booted into Recovery Mode and dropped into the console as root.
4 - Entered this to get into runlevel 3 to be able to stop the X server **telinit 3**.
5 - Entered this to stop the X server **sudo /etc/init.d/gdm stop**.
6 - Maneuvered to the directory where I had downloaded the driver **cd Downloads**.
7 - Entered this to install the driver - **sudo bash ./NVIDIA-Linux-x86_64-260.19.21.run**
8 - Started the X server via **sudo service gdm start** and I was already logged on, just had 
    to enter my password and all was well.
```If you are not absolutely sure, you might not want to try this. One time I messed it up and had to do a clean install :(
So, it's better to use the default drivers than have to do that!

---

