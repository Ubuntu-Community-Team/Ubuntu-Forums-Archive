---
title: "Nvidia HDMI blank screen"
date: 2010-07-10
forum: General Help
---

### Post by kenshinu on 2010-07-10
Hi everyone,

I had an install of xubuntu and I wiped it and put a fresh install of ubuntu 10.04 32 Bit.

I use it as a media centre. It's running of an Intel Atom 330 with Nvidia ION. All was running smoothly before I did this (which I am now wishing I didn't do).

My problem is that I have a blank screen via HDMI. Basic run down of what I have done:

Installed ubuntu via USB pen (using HDMI all was fine). I then go to install the new nvidia drivers (256 from their website) had some problems with the kernel stuff but got it to install all ok. Cue having a low res splash and blank/black screen. ctrl + alt + F1 I can access tty; so I try and start X using
```
sudo start gdm
```
Tells me it is already running so I try restart. I still have a blank screen.

Ok... So I try using VGA and it all works. Now I'm really confused. So, I load up nvidia settings and can detect the HDMI screen but when I try to use it, it doesn't work (the same problem as above).

Can anyone help me with this? 

Thanks in advance!

(Sorry if I posted this in the wrong section and if I missed the answer to this somewhere else)

---

### Post by dino99 on 2010-07-10
seems there are some issues

[http://www.google.com/search?as_q=ion%2Bhdmi%2Bnvidia%2Blucid&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=lang_en&cr=&as_ft=i&as_filetype=&as_qdr=y&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images](http://www.google.com/search?as_q=ion%2Bhdmi%2Bnvidia%2Blucid&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=lang_en&cr=&as_ft=i&as_filetype=&as_qdr=y&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images)

---

### Post by kenshinu on 2010-07-10
Hi, they are about sound. Not video. Thanks for your replay though.

---

### Post by dino99 on 2010-07-10
maybe better results with the latest drivers:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

or even more recent (and more instable too)

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

add and activate one of them into synaptic repo, then update

---

