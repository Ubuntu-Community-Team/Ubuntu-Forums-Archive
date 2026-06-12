---
title: "switched to kubuntu, now about to pull my hair out over wireless"
date: 2006-02-25
forum: General Help
---

### Post by harty83 on 2006-02-25
So I'm seeing that many are having issues with wireless.  I just did a reformat and installed kubuntu on my laptop.  Now, my wireless won't work.  I have a broadcom card installed via ndiswrapper.  My system recongnizes the card.  However, if I try to enable it, it immediatly automatically disables it (all this through kcontrol).  I've tried manually enabling it via ifup wlan0, but no go.  I've tried editing my /etc/network/interfaces and then ifup wlan0, no go.  I've tried everything I've found in the forums, no go.  Help anybody?  I'm going crazy.  I love kubuntu but am pretty sure I'm going to end up going back to gnome if I can't get this to work.

EDIT: oh yea, I've also tried to connect to my specific essid by adding wireless-essid *** to interfaces, but still not go.  My router is setup right (I've checked 3 times).  My wife is able to connect via winblows.

---

### Post by qalimas on 2006-02-25
I also have these wireless issues with my laptop's broadcom.  I got it working in GNOME, but not in KDE, regardless of how many KDE howtos I read.  I'd also like a good guide or hint as to what to do.

---

### Post by neoflight on 2006-02-25
**[this]("http://ubuntuforums.org/showthread.php?t=25683&highlight=broadcom+4306")** might help

---

### Post by harty83 on 2006-02-25
I've looked through that forum.  Its mostly for Gnome.  Did not find a solution.  I have also looked into all the driver's config files and all the RadioState is set the way it is suppose to be.

---

### Post by K-9 on 2006-02-25
I am awaiting my new laptop loaded with Kubuntu.

My first linux experience and the guy who sold it to me said notta problema and it will work with my airport extreme. Though he probably has never tried it.  After all of these hundreds of posts i have been pouring over it is looking like i probably did the wrong thing and these distros are just not ready for prime time.Way too, too, too many problems and issues and hassles. and I have not even botted up my new laptop yet.  Tthat was the reason i tried to get a laptop with all of this loaded and ready to go.I needed to have this laptop wireless and not hard wired - so if this is the case along with all of these other problems it is looking like I just threw all of this money away. Since i am a mac dude and not a windoze dude - this laptop may pretty much be useless it seems.

my windoze frustration days all over agin.


shit - tell me it is not so!

I am getting bummed very rapidly after visiting these many forums and threads.

---

### Post by FlakJacket on 2006-02-25
Well K-9 if it doesn't work you could always install ubuntu with gnome.  That seems to play nicely with wireless networking.

Flak

---

### Post by tadashi on 2006-02-26
I am not sure about the laptop you are using but I have a Sony Vaio VGN-TX670 and both Ubuntu and Kubuntu loaded up flawlessly.  The laptop is fairly new also so I was surprised.  However, I went through about 8 different distros (Slackware, Gentoo, Mandrake, Debian, RedHat v8 and 9, SUSE v9.3 and 10) until I found Kubuntu.

Test out the laptop and if it does not work get your money back.  Here is some info on Linux and laptops:
[http://www.linux-laptop.net/](http://www.linux-laptop.net/)
[http://tuxmobil.org/](http://tuxmobil.org/)

---

### Post by Randomskk on 2006-02-26
Not sure what tools all of you are using, but from the KDE menu:
Internet / Wireless LAN manager (KWifiManager)
That little program, once you enter some configs for it, seems to connect and moniter the connection happily. It's what I've used with KDE live CDs on wireless laptops.
..I wish I had a wireless laptop of my own :(

---

### Post by harty83 on 2006-02-26
I tried all the little programs I could find (wifi-radar, kwifimanager, kwirelessmonitor,etc) but none would pick up my network.  I tried using the command line also, and no go.

HOWEVER, the damnest thing happened.  I put in wife's pcmia wireless card (some off brand named Wave Buddy) and linux picked it right up.  I ejected it, and all of sudden MY internal wireless card was working!  Is there something about a card that the kernel supports that will cause a change to some file where as ndiswrapper or linuxant driver loader does not? (I bought driver loader out of desperation.  Used the 30 day trial thinking that maybe it was ndiswrapper that was the problem.  I thought that I had my wireless working b/c I saw my network's name, so I bought it.  Turned it out it was just where I had manually entered it and it wasn't acutally working. Note to self, fully test before assuming.  Oh well what's 20 bucks)

---

### Post by Rizado on 2006-02-26
[QUOTE=harty83]I tried all the little programs I could find (wifi-radar, kwifimanager, kwirelessmonitor,etc) but none would pick up my network.  I tried using the command line also, and no go.

HOWEVER, the damnest thing happened.  I put in wife's pcmia wireless card (some off brand named Wave Buddy) and linux picked it right up.  I ejected it, and all of sudden MY internal wireless card was working!  Is there something about a card that the kernel supports that will cause a change to some file where as ndiswrapper or linuxant driver loader does not? (I bought driver loader out of desperation.  Used the 30 day trial thinking that maybe it was ndiswrapper that was the problem.  I thought that I had my wireless working b/c I saw my network's name, so I bought it.  Turned it out it was just where I had manually entered it and it wasn't acutally working. Note to self, fully test before assuming.  Oh well what's 20 bucks)[/QUOTE]Sounds like a module that refuses to load until you plugg that pcmcia card in. Do lsmod when it isn't working and then again when you have entered pcmcia. Write the new modules down or something and load them one by one until you find the right one. Then add that module name into /etc/modules and it'll autoload at boot. Hopefully this will work.

---

