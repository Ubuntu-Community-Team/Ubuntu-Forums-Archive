---
title: "NVIDIA Multiple Configuration Questions - Nearly black /etc/X11/xorg.conf + more"
date: 2009-07-01
forum: General Help
---

### Post by EclipseAgent on 2009-07-01
I had some questions: 

Running Ubuntu 9.04 (i come from openSUSE so bare with me). 
Have NVIDIA 180.44 installed from repositories

/etc/X11/xorg.conf is nearly empty: 
$ cat /etc/X11/xorg.conf 

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

Why is that? 

This causes nvidia-settings to fail when trying to save config: 
bkevan@HCUBNT05006060:~$ sudo nvidia-settings

VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
Undefined Device "(null)" referenced by Screen "Default Screen".

Segmentation fault

Also, how can I make it so that my laptop when booted with screen closed, it disables the onboard and not considered a "clone" since the laptop screen supports higher resolution then the external monitor?

---

### Post by EclipseAgent on 2009-07-01
Ok.. I moved /etc/x11/xorg.conf and was able to write a new one.. guess I'll check to see if the configuration works.. a bit later.. 

Thanks in advance for any input.

---

### Post by .Maleficus. on 2009-07-01
IIRC, Ubuntu stopped using xorg.conf for nearly everything and leaves it all up to HAL to figure out at boot.  I don't use Ubuntu anymore so I could be wrong though.

---

### Post by EclipseAgent on 2009-07-01
> **.Maleficus. said:**
> IIRC, Ubuntu stopped using xorg.conf for nearly everything and leaves it all up to HAL to figure out at boot.  I don't use Ubuntu anymore so I could be wrong though.

I'm interested in knowing why you stopped using Ubuntu. From first shot.. I really think my experiences have been better with openSUSE, their buildservice allows for more updated applications etc through repositories. 

Ubuntu Jaunty doesn't have repository for VirtualBox OSE 3.0.0 (although you can use the VirtualBox closed source repository) 

There's no path to upgrade to Firefox 3.5 with a supported repository.. 

Just quite surprising that this gets all the attention etc it does, when it seems to be lacking so many of the basic functionality and ease of using updated apps etc..

---

### Post by .Maleficus. on 2009-07-01
I stopped using Ubuntu because it stopped being useful to me :).  I use Arch now which suits me much better because it comes with everything I need and nothing I don't.  Another reason I like Arch is because it's rolling release and I like having updates as soon as they are pushed to the repos (which is every day).  Ubuntu is a fine distro for someone new to Linux but it isn't suitable for me anymore.  Is there any reason you switched from openSUSE to Ubuntu?  It sounds like you had a pretty good time with it.

---

### Post by EclipseAgent on 2009-07-01
> **.Maleficus. said:**
> I stopped using Ubuntu because it stopped being useful to me :).  I use Arch now which suits me much better because it comes with everything I need and nothing I don't.  Another reason I like Arch is because it's rolling release and I like having updates as soon as they are pushed to the repos (which is every day).  Ubuntu is a fine distro for someone new to Linux but it isn't suitable for me anymore.  Is there any reason you switched from openSUSE to Ubuntu?  It sounds like you had a pretty good time with it.

Really I wanted to see what all the hype was about.. and just check it out. I got a new computer for work and decided to throw on Ubuntu 9.04 instead of openSUSE 11.1, just to .. well "try it out".. think I'll give it a fair run until openSUSE 11.2 goes GM or install when the LVM issues have been resolved.. 

I've heard some pretty good stuff about arch.. but haven't played with it yet. 

How stable are the updates pushed out to the rolling release repositories? ever have a problem with them? would you run them on a production work machine?

---

### Post by .Maleficus. on 2009-07-01
The only time I've ever had a bad update was from using packages in the [testing] repo which basically is filled with beta versions.  The [testing] repo isn't enabled by default so if you don't use it you shouldn't ever have a bad update.

As far as production/work machines go, I have Arch (without [testing]) running my server right now and it works great.

---

