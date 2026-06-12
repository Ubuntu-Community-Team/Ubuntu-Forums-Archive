---
title: "Fresh install of 11.10, problem with graphics drivers"
date: 2011-11-13
forum: General Help
---

### Post by nolag on 2011-11-13
I did a fresh install of 11.10 (had 11.04).  I tried to install graphics drivers and it fails and tells me to go to 

/var/log/jockey.log (attached in .tar.gz it was too big for a .txt)

I have tried the installation twice and am upset.  I don't know what to do or why I would have issues.  Also it has 195 updates it wants to do, but I told it to update during install...

Please help if you can this is urgent I need a linux distro for development at school and using their machines is slow (plus I like to have ubuntu)!

---

### Post by mörgæs on 2011-11-13
If you install and apply all updates but stick to the open source drivers, how does it work?

---

### Post by nolag on 2011-11-13
> **mörgæs said:**
> If you install and apply all updates but stick to the open source drivers, how does it work?


I want my eye candy (wobbly windows etc) but it goes too slow without the driver.  I am also worried because if this failed who knows what else might if I don't fix the problem :(.

---

### Post by mörgæs on 2011-11-14
You need to provide more information in order to narrow down the problem. After that you can focus on the eye-candy.

How did 11.10 work?
How did 11.04 work with open- and closed-source drivers?
Which graphics card do you have?

---

### Post by wowcolombia1 on 2011-11-14
Hey there,why dont you uninstall Ubuntu then installed again and dont play with the drivers,because i said it later that Ubuntu comes with alot of drivers and i think that it comes with the graphics drivers and all of those.

---

### Post by Mark Phelps on 2011-11-14
Not able to really understand the log -- since the text is all jammed together (which is why we ask folks to POST the log, using Code tags) -- but it appears to be looking BOTH for ATI and Nvidia drivers.

So, once again, we need to know the make and model video card.  If you don't know that, open a terminal, enter "lspci" -- and look for the line containing "VGA" -- and post the results back here.

---

### Post by nolag on 2011-11-15
Thank you all for trying to help.  I did 3 fresh installs (including the one that I posted about) and for some random reason it worked on the 3rd.  I have an ATI graphics card.  It worked flawlessly with the FGLRX drivers on 11.04, not sure why I needed to install 3 times to get it working now.

My computer lagged without it when I used wobbly windows.  Also it is much more power efficient to use the binary blobs (sorry the open ones are not as good, they don't seem to preform as well either).

Anyways, thanks again for trying to help :D.  Now all I need to do is get over the fact that a 3D cube is not easy to setup and get used to unity :P.

---

### Post by mörgæs on 2011-11-15
Good that it worked. If you don't like Unity, Xubuntu is worth trying.

A small correction: Everything in Buntu is a binary file. In a normal installation you don't get to see the source code. You can easily find it if you want, but it is not there by default, since most users can't edit it anyway.

---

### Post by nolag on 2011-11-16
> **mörgæs said:**
> Good that it worked. If you don't like Unity, Xubuntu is worth trying.

A small correction: Everything in Buntu is a binary file. In a normal installation you don't get to see the source code. You can easily find it if you want, but it is not there by default, since most users can't edit it anyway.

Binary blob to me is if the source is not available.  I can get the source for any of the open drivers.  Xubuntu is xfce, I like gnome.  xfce is not as shiny.  I am giving unity a try because until you know something it seems bad.  I hated ribbons on windows now I like them.  I will give it a month or two.

---

