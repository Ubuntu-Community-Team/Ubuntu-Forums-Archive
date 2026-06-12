---
title: "A couple of questions for a Ubuntu newbie"
date: 2006-05-23
forum: General Help
---

### Post by chrroessner on 2006-05-23
Hi,

first of all: I switched my system from Gentoo Linux AMD64 to Ubuntu 32-Bit Dapper Drake. After having lots of trouble getting Dapper installed with graphical installer (LVM broken?), I finally have some questions:

1.) I do not know why, but ALSA 1.0.10 is absolutley bad (was the same under Gentoo). I really need 1.0.11 for my SB Live 5.1 sound card, because the sound support for my saa7134 tv card is left channel mono with this alsa release and because of Gentoo I know that the newer release fixed that. So I installed pbuilder and stuff, did pbuild create and got the alsa-base files from Debian unstable. But I do not know how to build ubuntu packages?

2.) lineakd is too old. I need support for LTUFBL, which only exists in a newer version (Do not know which at the moment)

3.) **Most important for me**: I have a AVM B1 active card in my machine. Although I installed avm-fritz-firmware-2.6.15-23, I could not find the b1.t4 firmware. So I downloaded it and placed it under /usr/share/isdn/2.6.15-23.Even tried under /lib/firmware/isdn and /lib/firmware/2.6.15-23 and /lib/firmware/2.6.15-23/isdn. Each time rmmod b1pci, b1dma, b1 and modprobing again. Without this firmware the capi stuff does not work and I will not get capisuite started successfully :-(

I really would be happy to have information on how to compile some packages for myself (or using other repositories, whatever)

I am not a Linux newbie but Ubuntu/Debian :-) Hope to get a friend of this distribution

Kind regards
Christian

---

### Post by Sef on 2006-05-23
> 1.) I do not know why, but ALSA 1.0.10 is absolutley bad (was the same under Gentoo). I really need 1.0.11 for my SB Live 5.1 sound card, because the sound support for my saa7134 tv card is left channel mono with this alsa release and because of Gentoo I know that the newer release fixed that. So I installed pbuilder and stuff, did pbuild create and got the alsa-base files from Debian unstable. But I do not know how to build ubuntu packages?

Check out these two sites:

[http://monkeyblog.org/ubuntu/installing.html]("http://monkeyblog.org/ubuntu/installing.html")

[http://www.psychocats.net/ubuntu/installingsoftware.php]("http://www.psychocats.net/ubuntu/installingsoftware.php")

---

