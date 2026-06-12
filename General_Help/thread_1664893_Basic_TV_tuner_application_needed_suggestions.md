---
title: "Basic TV tuner application needed? suggestions?"
date: 2011-01-11
forum: General Help
---

### Post by Sweetdaddydong on 2011-01-11
I have a media center PC that I used to watch TV from a cable box from. I am switching from windows to linux and would like a simple and easy to use program that will allow me to just watch TV. All I really need is channel 3 so I can watch the cable box.

Any suggestions?

---

### Post by KuriKai on 2011-01-11
Me-tv might be the right program for you maybe
[https://launchpad.net/me-tv](https://launchpad.net/me-tv)

---

### Post by Sweetdaddydong on 2011-01-11
> **KuriKai said:**
> Me-tv might be the right program for you maybe
[https://launchpad.net/me-tv](https://launchpad.net/me-tv)

This looks promising. I'll give it a shot. Are there any other options that are part of the standard Ubuntu repositories.

---

### Post by Sweetdaddydong on 2011-01-27
So I tried it. Couldn't get it to work. NOt sure if I am doing something wrong. I am not even sure how to trouble shoot. Any suggestions?

---

### Post by AlphaLexman on 2011-01-27
You could look at: [tvtime]("http://tvtime.sourceforge.net/")
or
[linuxtv]("http://www.linuxtv.org/")

---

### Post by Trublue on 2011-01-27
Mythtv another which is the only one I got to work.Had to install Linux non-free firmware before my media card would work

---

### Post by Sweetdaddydong on 2011-04-09
So I've tried linuxTV, TVtime and MythTV and none seemed to have worked. I am wondering if I am missing an important step here. 

Would I have better luck installing Mythbuntu?

---

### Post by AllGamer on 2011-04-25
> **Sweetdaddydong said:**
> So I've tried linuxTV, TVtime and MythTV and none seemed to have worked. I am wondering if I am missing an important step here. 

Would I have better luck installing Mythbuntu?

if MythTV didn't work for you then Mythbuntu wont make much of a difference, as it's basically the same OS (ubuntu + MythTV interface)

your best bet is TvTime by far that's the easiest to get up and running, if TvTime doesn't work for you, then chances are the TV turner card you are using might have not been installed / detected by ubuntu during boot time.

if the TV Turner installed is a PCI card, you can run **sudo lspci** to see if it's listed, if it's a USB device, then try **sudo lshw -businfo** and see if it's listed

if it doesn't show up at all, then you'll first have to find or compile the proper drivers for the TV Tuner you are trying to use.

---

### Post by Sweetdaddydong on 2011-05-21
> **AllGamer said:**
> if MythTV didn't work for you then Mythbuntu wont make much of a difference, as it's basically the same OS (ubuntu + MythTV interface)

your best bet is TvTime by far that's the easiest to get up and running, if TvTime doesn't work for you, then chances are the TV turner card you are using might have not been installed / detected by ubuntu during boot time.

if the TV Turner installed is a PCI card, you can run **sudo lspci** to see if it's listed, if it's a USB device, then try **sudo lshw -businfo** and see if it's listed

if it doesn't show up at all, then you'll first have to find or compile the proper drivers for the TV Tuner you are trying to use.

The card I have is a PCI card. 
I used "sudo lspci" and found in the output this line,

03:06.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)

The video card I have is an older Hauppauge card. So this line makes me think that might be it because it says iTVC16 in it but am not 100% because I don't see Hauppauge anywhere. 

So now where do I go from here? Everytime I try to run TVTime it just instantly crashes.

---

### Post by crispy_420 on 2011-05-21
tvtime and hauppauge will not work. Strangely it works well with low end tuner cards that do not have a hardware encoder like old WinFast cards.

Hauppauge is listed indirectly. That CX23416 is the chipset info for the device.

---

