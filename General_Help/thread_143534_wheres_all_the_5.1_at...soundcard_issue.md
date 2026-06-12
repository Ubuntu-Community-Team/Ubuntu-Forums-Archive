---
title: "wheres all the 5.1 at...soundcard issue"
date: 2006-03-12
forum: General Help
---

### Post by eXidos on 2006-03-12
I just installed my C-Media CMI8738-mc6 card, the driver auto installed and the sound worked fine untill I tried to play and dolby digital movie, however I am not getting and center chanel on music, I have checked, dubble checked and checked once more that all the cable are installed proporly and they are..

exidos@EXBOX:~$ sudo lspci -v | grep audio
0000:02:01.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)


I am getting audio only through the rear out and it is putting out rear left/right and LFE because my sub is pumping along with the movie.

I have not edited and scrips or changed and settings my self but my volume control shows that I do have this card installed. did I miss a step?

My speakers (Altec Lansing 5100) have 3 settings sterio x2, 4.1 gaming, and 5.1 I am using 5.1

Is their a 5.1 decoder that I need? I am using ALSA...

---

### Post by eXidos on 2006-03-12
ok i got the fronts, rears, and sub going but the center now seems like it wants to be a sub as well...all i did was tell the line in and mic to use a differant jack but still no center

---

