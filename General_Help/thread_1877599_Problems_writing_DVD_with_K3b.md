---
title: "Problems writing DVD with K3b"
date: 2011-11-08
forum: General Help
---

### Post by tech291083 on 2011-11-08
Hi,

I am having problems writing DVD/CD using the latest version of K3b on my Ubuntu 10.10 installation. I have attached an image of the program with its error message to this thread. Please help me out, thanks.

---

### Post by TeoBigusGeekus on 2011-11-08
What are you trying to burn? (data, iso, etc.)

---

### Post by tech291083 on 2011-11-08
> **TeoBigusGeekus said:**
> What are you trying to burn? (data, iso, etc.)


Every thing - data, images, video, audio, iso, pdf, text files. But still can't burn anything. Help is deeply appreciated. Thanks

---

### Post by TeoBigusGeekus on 2011-11-08
Have you tried brasero?

---

### Post by QLee on 2011-11-08
> **tech291083 said:**
> 
I am having problems writing DVD/CD using the latest version of K3b on my Ubuntu 10.10 installation. I have attached an image of the program with its error message to this thread. Please help me out, thanks.
Well, what I would do is pay attention to the error message the application gave you which is shown in your first screenshot.

It might be something that is optioned on the K3B settings menu, perhaps something in the Setup Systems Permissions as that is what the error refers to. Always pay attention to what the system tells you.

---

### Post by tech291083 on 2011-11-09
> **TeoBigusGeekus said:**
> Have you tried brasero?

I am actually trying to write an iso of the recently downloaded Debian 6.0.3 (i386 DVD iso image 4.4 GB) 
Yes,  I did try it as well and used the option called Burn Image and to my  surprise it worked. The iso image was written successfully twice when I  used a brand new DVD-R and then a brand new DVD-RW. But despite changing  the bios settings I am not able to boot my pc off them at all for me to  be able to install them. 

I also again tried K3b and used the option Burn Image on the Tools menu and I was able to write the iso image successfully this time. But I could not boot my pc using this DVD-R as well despite changing the boot sequence in the BIOS. It is really funny now as initially I was not able to write to a DVD and now I am not able to boot off it for some weird reason, can anyone please help? Thanks

---

### Post by tech291083 on 2011-11-09
Here is where I have downloaded my iso image of the latest Debian distro from. Thanks

[debian-6.0.3-i386-DVD-6.iso.torrent]("http://cdimage.debian.org/debian-cd/6.0.3/i386/bt-dvd/debian-6.0.3-i386-DVD-6.iso.torrent")  


[http://cdimage.debian.org/debian-cd/6.0.3/i386/bt-dvd/](http://cdimage.debian.org/debian-cd/6.0.3/i386/bt-dvd/)

---

### Post by QLee on 2011-11-09
[QUOTE=tech291083]Here is where I have downloaded my iso image of the latest Debian distro from. Thanks

[debian-6.0.3-i386-DVD-6.iso.torrent]("http://cdimage.debian.org/debian-cd/6.0.3/i386/bt-dvd/debian-6.0.3-i386-DVD-6.iso.torrent")  


[http://cdimage.debian.org/debian-cd/6.0.3/i386/bt-dvd/](http://cdimage.debian.org/debian-cd/6.0.3/i386/bt-dvd/)[/QUOTE]

Well tech, from what you wrote it appears that you downloaded the 6th DVD in the set.

From the FAQ at :
[http://www.debian.org/CD/faq/#bootable](http://www.debian.org/CD/faq/#bootable)
> **The CD/DVD fails to boot! / From which CD should I boot?**
 Only the first CD/DVD in a set is bootable.


I'm not sure this forum is the best place to cover Debian install issues, you might want to consider posting on a Debian forum in an "install" sub forum to get the help from people with Debian experience.

---

### Post by tech291083 on 2011-11-09
> **QLee said:**
> Well tech, from what you wrote it appears that you downloaded the 6th DVD in the set.

From the FAQ at :
[http://www.debian.org/CD/faq/#bootable](http://www.debian.org/CD/faq/#bootable)


I'm not sure this forum is the best place to cover Debian install issues, you might want to consider posting on a Debian forum in an "install" sub forum to get the help from people with Debian experience.


This is really funny, but I have done the same with a previous version a year ago and it too was DVD link no 5 or 6 what appeared tto be a set just like this time and it did boot after I downloaded it. I am sorry if by mistake I have asked a Debian related issue here, but I was just making sure that I let you know as to what exactly I was trying to write using K3b to get a better solution to my problem. You really have given me a good and though-provoking anwser, so I will try to download the 1st DVD then. I never knew this. And to be honest this is a bit weird as one would just think that all the 6 etc links are just a list many mirrors available. Thanks.

---

