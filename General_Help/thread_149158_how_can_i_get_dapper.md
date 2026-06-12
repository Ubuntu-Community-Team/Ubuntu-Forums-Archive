---
title: "how can i get dapper"
date: 2006-03-23
forum: General Help
---

### Post by njzillest on 2006-03-23
how do i get drake? is there a way i can just patch breezy without reinstaling anything?


also if i dont like it can i  just downgrade the OS without reinstalling it?


also is its wireless configured like breezy (ipw 2200)

---

### Post by dragonfyre13 on 2006-03-23
A. apt-get dist-upgrade

B. No.

C. no clue.

Thought I would at least answer what I know, since you posted this so long ago, with no answer.

---

### Post by Ramses de Norre on 2006-03-23
1.
sudo gedit /etc/apt/sources.list  and change 'breezy' to 'dapper' in all url's.
Sudo apt-get update && sudo apt-get dist-upgrade

2.
It will probably work if you change everything back to breezy in your sources file and dist-upgrade again but I never tried that before.

3.
Dapper should be at least as good pre-configured as breezy, so I guess it will ;)

PS: just because you ask this, I doubt you're ready for dapper. It's still a development version.. I might be wrong and you might be ready to try that. But I just want to warn you before. If you haven't got many linux/ubuntu experience I'd wait untill june when dapper will be officially released.

---

### Post by int on 2006-03-23
Why this thread about Dapper in "Ubuntu 5.10 Support (GNOME) " ? find Dapper thread.

---

### Post by njzillest on 2006-03-23
there is no dapper thread


I know my ropes of Ubuntu but im no guru. I know how to install from source, deb and rpm. I know alot of other things..


but now thinking about it, it could messup my computer, for im not experianced enough. 


thanks alot for the advice :mrgreen:

---

### Post by njzillest on 2006-03-23
is it very buggy??


i do know how to program. I Know C++ HTML and python. (still learning python at a rapid rate)

---

### Post by Ramses de Norre on 2006-03-23
Not everything is totally debugged I assume, and not everything is tested enough. But there are people running a stable dapper allready, you're just more llikely to crash the OS or to encounter difficult issues when using a development release.

(In fact there is a dapper forum [http://www.ubuntuforums.org/forumdisplay.php?f=111]("http://www.ubuntuforums.org/forumdisplay.php?f=111")  where they probably know more about dapper ;))

---

### Post by anodizer on 2006-03-23
[QUOTE=njzillest]
also if i dont like it can i  just downgrade the OS without reinstalling it?
[/QUOTE]

Backup your breezy install following [this method](http://www.ubuntuforums.org/showthread.php?t=81311) and you can restore it anytime safely. Be aware though, you must delete every single file and then restore the backup to have your breezy back running properly (if something goes wrong you can always boot with a live cd).

---

