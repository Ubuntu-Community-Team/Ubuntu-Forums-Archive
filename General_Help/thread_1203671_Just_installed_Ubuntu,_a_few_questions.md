---
title: "Just installed Ubuntu, a few questions"
date: 2009-07-03
forum: General Help
---

### Post by Matt P on 2009-07-03
I had been playing around with Ubuntu on my friends computer and really enjoyed it. Seeing how my__ windows xp was virus filled and was in needing of a reformat I thought I may as well finally make the switch over to linux.

I have installed Ubuntu quickly with no errors and did a format on my 30GB hard drive __ before hand. It is up and running smoothly but I have just a few newbie questions for you guys

I have my 30GB hard drive which the OS is installed on showing up fine. However I also have an 80GB hard drive which I use for music and games that isn't showing up anywhere. Is there something I need to do so that my second hard drive will be recognized?

Secondly I'm not sure which audio/video drivers I'll need to install to be able to play music/movies, play games etc. I have a JVC sterio system connected to my computer via USB but cant seem to get audio playing.

Also, I'm unsure of which hardware I have, does Ubuntu have its own version of 'dxdiag' to find this out?

Any help for this linux newb is much appreciated

thanks in advance

---

### Post by earthpigg on 2009-07-03
applications->accessories->terminal

and type 'sudo apt-get install ubuntu-restricted-extras' to enable youtube, mp3, etc playback.

are you sure the 80gb hard drive isn't showing up in places->computer? it will be called '80 GB Media' or something like that.

to probe for hardware, play around with:

hwinfo
lspci

for any linux command-line tool, typing 'man whatever' to get the manual for it.

example:

man hwinfo


pressing q closes the manual

---

