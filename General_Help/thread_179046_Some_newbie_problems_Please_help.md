---
title: "Some newbie problems Please help"
date: 2006-05-18
forum: General Help
---

### Post by aman_pervaiz on 2006-05-18
Hi I am a newbie and after two weeks of toil, I am finally beginning to get comfortble with this nice OS. There are a few things that I'm having trouble with.

1.) My cds and dvds have stopped automounting for some reason. I think it was after running Automatix but I'm not sure. When I insert my dvd then I have to go to places --> computer --> right click the cd drive and eject. Then after inserting the cd/dvd again I have to right click and mount. Is it supposed to be this way. I'm not sure. I don't really mind doing this everytime but would sure love automounting. Sorry for being lazy :)

2.) My USB drive used to mount on my previous ubuntu (this ubuntu installation is my fourth --messed my windows partion twice :-)  ). The drive does not mount anymore (it still does in windows though). I don't know where I messed up. How can I debug this problem?

3.) Most of the times, while running media players I get a problem with /dev/dsp. I have to use "sudo  /bin/fuser -v /dev/dsp" and similar commands to get rid of he problem. Is there an easier automatic way perhaps. Is it a problem with my stupid hardware? Also when I am using audacity and trying to record sound from my dvd for example, audacity just won't record and gives /dev/dsp problem. Is it because since dvd decoders are using the sound system so audacity cannot. Is that the problem? Is there a work around?

4.) Can I get text along with the icons  in the panel. I mean every icon having a small text label at the bottom. Is that possible? Please ignore this if i'm asking for a stupid thing. Its just that i like labels along with icons :D

5.) Is there a dvd burner that can verify data after its written (like nero) ?

Thats all. Everything else is going perfect and am enjoying the experience. Hats off to the developers :-)

Also will there be support for wpa soon. Unfortunately the wpa supplicant didn't work for me and I am now being forced to use an open wireless connection (my router doesn't like wep and crashes). I feel very unsecure with this.

BTW I have an inspiron 700m notebook with ubuntu breezy.

---

### Post by slimdog360 on 2006-05-19
[QUOTE=aman_pervaiz]

5.) Is there a dvd burner that can verify data after its written (like nero) ?

.[/QUOTE]

You can get nero for linux, I havent used it though.

---

### Post by aman_pervaiz on 2006-05-19
Thank you for the reply but I was looking for a free software. This is one of the reasons I started using ubuntu anyway.

---

### Post by dg_w on 2006-05-19
If I rember correctly xcdroast is the the universe repos ?

that does a verify

---

### Post by savas on 2006-05-19
> 1.) My cds and dvds have stopped automounting for some reason. I think it was after running Automatix but I'm not sure. When I insert my dvd then I have to go to places --> computer --> right click the cd drive and eject. Then after inserting the cd/dvd again I have to right click and mount. Is it supposed to be this way. I'm not sure. I don't really mind doing this everytime but would sure love automounting. Sorry for being lazy :).

2.) My USB drive used to mount on my previous ubuntu (this ubuntu installation is my fourth --messed my windows partion twice :-)  ). The drive does not mount anymore (it still does in windows though). I don't know where I messed up. How can I debug this problem?

Look at System->Preferences->Removable Drives And Media. There is a check box, Browse medium when insterted.

---

### Post by aman_pervaiz on 2006-05-19
[QUOTE=dg_w]If I rember correctly xcdroast is the the universe repos ?

that does a verify[/QUOTE]



Thanx for the recommendation. I tried that but first of all I don't think that it burns dvds and secondly it has refused to detect my drive and has given me some error saying that I need to enable scsi emulation in the kernel ](*,)

---

### Post by dg_w on 2006-05-19
Umm#

[http://perso.wanadoo.fr/bonfire/features.htm](http://perso.wanadoo.fr/bonfire/features.htm)

[http://ubuntuforums.org/showthread.php?t=175536&highlight=cd+verify](http://ubuntuforums.org/showthread.php?t=175536&highlight=cd+verify)

?

---

### Post by aman_pervaiz on 2006-05-19
[QUOTE=savas]Look at System->Preferences->Removable Drives And Media. There is a check box, Browse medium when insterted.[/QUOTE]


I am sorry but on my system when I do System --> Preferences ...then there is no "Removable Drives and Media" option. BTW I am using ubuntu 5.10 breezy. Do I need to install anything for this option to appear.

---

### Post by aman_pervaiz on 2006-05-19
[QUOTE=dg_w]Umm#

[http://perso.wanadoo.fr/bonfire/features.htm](http://perso.wanadoo.fr/bonfire/features.htm)

[http://ubuntuforums.org/showthread.php?t=175536&highlight=cd+verify](http://ubuntuforums.org/showthread.php?t=175536&highlight=cd+verify)

?[/QUOTE]


Excellent. This looks really good. I shall give it a try. :)  Thank you guys.

---

### Post by aman_pervaiz on 2006-05-19
[QUOTE=aman_pervaiz]I am sorry but on my system when I do System --> Preferences ...then there is no "Removable Drives and Media" option. BTW I am using ubuntu 5.10 breezy. Do I need to install anything for this option to appear.[/QUOTE]


Yipeeeeee....*dancing with joy*...finally got auto-mount to work....Basically I installed gnome- volume-manager from the pakages and it solved my mounting problems...:mrgreen:

---

### Post by aman_pervaiz on 2006-05-19
Well...my sound problems are also almost solved thanks to this guide 
[http://ubuntuforums.org/showthread.php?t=32063&highlight=alsa](http://ubuntuforums.org/showthread.php?t=32063&highlight=alsa)

What beats me is that why isn't this a default in gnome. Probably this is not polished enough?

---

