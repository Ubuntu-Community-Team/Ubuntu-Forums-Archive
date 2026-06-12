---
title: "segmentation fault in xine, mplayer and xmms"
date: 2006-02-15
forum: General Help
---

### Post by tfotherby on 2006-02-15
The following multimedia players do not start up and cause a segmentation fault: xine, mplayer and xmms. However ffplay, aviplay and realplay work ok.

Does anyone know which library xine, mplayer and xmms have in common? and do you think re-installing that library will solve my problem?

Any help would be appreciated.

(This is nearly a dupe of [http://www.ubuntuforums.org/showthread.php?t=120854&highlight=segmentation+fault+xine](http://www.ubuntuforums.org/showthread.php?t=120854&highlight=segmentation+fault+xine) except the problem occurs whether I run the applications with sudo or as a regular user.)

---

### Post by heimo on 2006-02-15
Does glxgears and vlc segfault, too? (if you have those installed) 

Spector had a weird, similar problem:
[http://www.ubuntuforums.org/showthread.php?t=129147](http://www.ubuntuforums.org/showthread.php?t=129147)

---

### Post by tfotherby on 2006-02-15
Heimo, Thank you. I've been unable to watch TV for ages and you solved it for me. It's people like you that do wonders for the Linux community. =D> 

Just this one little command fix's it:

sudo touch /etc/ld.so.nohwcap

---

### Post by heimo on 2006-02-16
If anyone can explain why this solves the problem, I'd be greatful to hear it. I read some discussion about hwcap, but didn't really understand much about it. I'm always a bit wary if I can't understand solution / background to some problem. #-o

Oh, and thank you tfotherby for the kind words. Big thanks go to all the Ubuntu and Debian devs and Ubuntuforum mods and regulars. Oh, and [Mark]("http://www.markshuttleworth.com/").

---

