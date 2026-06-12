---
title: "uTorrent under wine using 100% cpu"
date: 2006-05-19
forum: General Help
---

### Post by Melciah on 2006-05-19
can anyone tell me why? anyone know how to correct the problem?

the really annoying part of this is that i had it running perfectly under my last breezy install.

---

### Post by ProjectGod on 2006-05-19
no easy answer. but WINE takes out more system resources than software that's straight through compatible on a linux system... therefore i guess you could try using other bittorrent packages that can dock straight onto linux without wine. 

the following link will contain may p2p, torrent apps.
[http://ubuntuforums.org/showthread.php?t=33183](http://ubuntuforums.org/showthread.php?t=33183)

hope this helps.

---

### Post by YokoZar on 2006-05-19
[QUOTE=Melciah]can anyone tell me why? anyone know how to correct the problem?

the really annoying part of this is that i had it running perfectly under my last breezy install.[/QUOTE]
This occured on some of the older Wine packages.

Are you running the latest Wine available from here: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) ?

---

### Post by Melciah on 2006-05-19
updating wine fixed the problem. its running beautifully again. Cheers.

i really don't understand it, even under wine, utorrent is the best client ive ever used. native linux clients ive found to be pretty useless. they either lack features, are too resource intensive, or simply dont work.

thanks for the help guys.

---

### Post by cacharreo on 2006-05-19
Why do you use windows aplications under Linux?:confused: 
Please, use Linux native applications. it should be better!!!!](*,)

---

### Post by Bd0g on 2006-05-19
[QUOTE=cacharreo]Why do you use windows aplications under Linux?:confused: 
Please, use Linux native applications. it should be better!!!!](*,)[/QUOTE]
Hehe, should be.. but utorrent kicks a.s.s. You go with what makes your world spin.

Even if it's spawned in the MS enviroment :twisted:

---

### Post by underwater on 2006-05-19
[QUOTE=cacharreo]Why do you use windows aplications under Linux?:confused: 
Please, use Linux native applications. it should be better!!!!](*,)[/QUOTE]


I don't use utorrent with wine, but I can say that Azureus and the other clients have NOTHING on utorrent.

I don't know how advantageous it is to use wine with utorrent, though, like the original poster is doing.  One of the beautiful parts about utorrent was that it was a small program that had very small memory and cpu usage.  I think that running wine with it would pretty well negate any positives cpu or memory benefits that would normally come with running utorrent.  I run Azureus, but I'm not happy with it.  I would much rather be running a kind of middle of the road client.  More features than the orginal python client, but also with less bloat and features than Azureus.  I'm pretty sure Azureus can do the dishes for me while downloading a torrent.  :-/

---

### Post by ashmew2 on 2007-02-21
but ktorrent is also a pretty pretty good bittorrent client :)

---

### Post by jonahmano on 2007-04-06
U-Torrent is a very good software which doesn't even touch the CPU processor. The problem is with any other software making U-Torrent the scape goat. 

The remedy for this is download Process Explorer from [www.sysinternals.com](www.sysinternals.com) and run the Process Explorer EXE file and you can see which all softwares using the amount of  CPU. 


Select the software (it has to be unknown or least important one) which is using great amount of CPU other than U-torrent and using right clicking mouse, Kill it and you can see the CPU usage of U-torrent becoming Zero.

Thanks

---

### Post by NoobieDoobieDo on 2007-07-04
Thanks for the tips.  I had ubuntu 7.04 and wine + utorrent and it worked fine.  Now I'm on Ubuntu 6.06 and wine + utorrent = 100% cpu usage.

After I upgraded everything is peachy.

---

### Post by Hallvor on 2007-07-04
I found kTorrent to be quite good and looking almost identical to uTorrent. Just hope you guys don`t use the latest version of uTorrent, since it is owned by Bittorrent Inc, affiliated with the MPAA.

---

