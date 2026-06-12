---
title: "Burning dvd backups on 4.7 disks!"
date: 2011-05-16
forum: General Help
---

### Post by johnburr54 on 2011-05-16
I've always found these forums to be very friendly and I do appreciate that. I really love the latest release of Ubuntu, 11.04.
The reason I'm here today is because wine seems to have changed quite a bit. It used to be simple and I only need it for a couple of programs called dvd decrptor and dvd shrink.
I've tried some programs in linux and haven't been able to get them to work, like DVD 5. It could be me, of course!:P
So, I haven't been able to get wine to read my cd-rom hardware to where I can back up my dvds. 
Are there any solutions that anyone knows of on Wine or linux programs which I prefer? I did create an iso from a dvd with DVD 5, I believe, and then had it set up to burn with k3b.
The first part of the dvd came up with the menus and music, but I could go no further than that. I figure there is some little something that I'm doing wrong or some bit of linux software suport for DVD 5 or k3b that I do not have. That's usually what it is. Sometimes I can get the answers from the pages on the programs, other times not and that is when I come here to you good people.
So if anyone has any answers, Please fill me in! Thank you! :)
John

---

### Post by gsmanners on 2011-05-16
You shouldn't have any trouble with [DVD Decrypter]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1558") in Wine. [DVD Shrink]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1533") should also work fine. If you're comfortable with those apps, I would suggest you stick with them.

That said, you might check out DeVeDe in Software Center or Synaptic. Just make an ISO file and then burn it with Nautilus or Brasero or K3b (or whatever you want).

---

### Post by mc4man on 2011-05-16
For dvd's without recent structure protection (last 3 yrs. or so) DVDD will work fine.
Don't happen to have here but if you open it up somewhere in it's tools/settings/options/preferences (whatever it's called in DVDD) you'll find an option for I/O
Set it to ASPI_WNASPI32.DLL 
Then DVDD will detect your drive(s) independent of wine's config or lack of

(screen shows the setting in ImgBurn, - same author  so I know it's in DVDD
I'd use ImgBurn to burn your 'shrinked' titles over any other available app or prog. - no comparision whatsoever

---

### Post by johnburr54 on 2011-05-17
> **gsmanners said:**
> You shouldn't have any trouble with [DVD Decrypter]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1558") in Wine. [DVD Shrink]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1533") should also work fine. If you're comfortable with those apps, I would suggest you stick with them.

That said, you might check out DeVeDe in Software Center or Synaptic. Just make an ISO file and then burn it with Nautilus or Brasero or K3b (or whatever you want).


I simply am unable to get wine to work with my cd rom drive. As I've roamed aromd the web looking for an answer I read posts where other people can't either and the solutions aren't clear enough for me to understand. I tried some of them. DeVeDe didn't work either. It looked liked it was going to make an iso and stopped abruptyl as it was burning the iso to disk. I'm not sure why on that one either! Thsnk you got ytyinh yo hrlp!

---

### Post by wildmanne39 on 2011-05-17
> **johnburr54 said:**
> I simply am unable to get wine to work with my cd rom drive. As I've roamed aromd the web looking for an answer I read posts where other people can't either and the solutions aren't clear enough for me to understand. I tried some of them. DeVeDe didn't work either. It looked liked it was going to make an iso and stopped abruptyl as it was burning the iso to disk. I'm not sure why on that one either! Thsnk you got ytyinh yo hrlp!
Hi, go here and follow the instructions for the version of ubuntu you have and it should work fine.  [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by johnburr54 on 2011-05-17
> **mc4man said:**
> For dvd's without recent structure protection (last 3 yrs. or so) DVDD will work fine.
Don't happen to have here but if you open it up somewhere in it's tools/settings/options/preferences (whatever it's called in DVDD) you'll find an option for I/O
Set it to ASPI_WNASPI32.DLL 
Then DVDD will detect your drive(s) independent of wine's config or lack of

(screen shows the setting in ImgBurn, - same author  so I know it's in DVDD
I'd use ImgBurn to burn your 'shrinked' titles over any other available app or prog. - no comparision whatsoever

This worked. ImgBurn also had to be set to AsPi_WNASPI32.DLL and I still had to go through dvd shrink to get it down to a burnable size, but hey, thank you. With your help the problem was solved.

---

### Post by mc4man on 2011-05-17
> **johnburr54 said:**
>  I still had to go through dvd shrink to get it down to a burnable size.
ImgBurn is mainly a iso creation and or  burning app for anything , it can also read (rip) non-protected discs (audio, data cd's. data dvd's, non protected video disks, ect.

After DVDD was taken from LIGHTNING UK by Macrovision/Sony he started ImgBurn but obviously had to stay on the clearly 'legal' side

---

### Post by deserthowler on 2011-05-17
For me k9copy does the trick every time in Linux.

Earl

---

