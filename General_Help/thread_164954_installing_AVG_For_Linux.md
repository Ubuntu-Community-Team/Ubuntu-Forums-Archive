---
title: "installing AVG For Linux"
date: 2006-04-23
forum: General Help
---

### Post by MarvinZurcher on 2006-04-23
When I launch AVG For Linux Workstation I get thios error message.AVG for Linux was not registred, please register it with valid license number. I enter 70FREE-tx-IB-p1-CO1-S139FC-327-9FPB when I installed the program, but it didn't work. Does anybody know what I did wrong? Thank you in advance

---

### Post by colo on 2006-04-23
Are you REALLY sure you'd want to have a anti-virus-solution installed and running on your PC? That's something I commonly notice when users switch over from windows, they can't get rid of some of their old habits ;)

You really don't need "protection" like this, I would not take the risk and let a proprietary program not subject to peer-reviewing as root on my box. That's a far greater risk than any Linux-virii spreading in the wild in my opionion.

If you're about to scan for windows-virii only (on a fileserver or something, probably), then you should go take a look at ClamAV. It gets done what is needed to portect windows clients from various threats they suffer from so frequently.

---

### Post by Golden Warrior on 2006-04-23
I agree.  I just use ClamAV.  Unlike Windows there just aren't as many viruses that can affect Linux.

However that's a moot point.  As for your problem, are you using a license number that's valid on the Windows version?  If so that could be the problem.  I don't use AVG, but they could require different numbers for Windows and Linux.

---

### Post by MarvinZurcher on 2006-04-23
When I click OK on the error message that says AVG is not registered the window goes away and there is no place to register.](*,) ](*,)

---

### Post by Sef on 2006-04-23
Another reason could be that the registration number is too old and has expired.   They usually are only good for about 24 hours.

---

### Post by sinkxdie on 2006-04-23
I would get Avast Antivirus for linux, I have it now.
Its fast and really good, even though there aren't ever viruses on my Linux, its still good to have it.

---

### Post by Nordoelum on 2006-04-23
Why would you NOT recommend a virus protection software for linux? The treath is still there, even though there is only a few cases of virus infection..

---

### Post by colo on 2006-04-23
The "threat" is almost non-existant. I'd consider the "threat" of a proprietary (one you can not view the source of!) application running with elevated privileges a higher risk than the possibility of a widespread virus-infection of such a scattered system like GNU actually is. Who's telling you that $COMPANY does not do some evil stuff to manipulate or collect your data with its "free security tool", esp. when it's running with UID 0? That task could do virtually ANYTHING on your box without you ever knowing about. If you hose your system via a virus, which is, I again STRONGLY proclaim, somwhere in between of _HIGHLY_ unlikely and downright impossible, you're just losing the stuff of the user you're logging in as. If there's other family members or co-workers registered on the system, and they got their permissions set up in a sane manner, there's no way to interfere with their data. A root-powered daemon application is not limited by ANY (non-SELinux) imposed access restrictions, and might be spying on you, or doing things even worse which I'll leave to your imagination.

All of the above, and the fact that it consumes system resources you could and should spend otherwise, should deprive you from the urge to install Avast and/or AVG Antivirus on your GNU/Linux-powered system. Leave those applications to Windows-users, they seem to desperately need them. You can make use of chrootkit to periodically check your system for ACTUAL threats GNU/Linux-systems may face in everyday life.

---

### Post by Nordoelum on 2006-04-23
If antivirus software is using root, there is something wrong with linux, as I would see it. Please explain otherwise.

---

### Post by dmizer on 2006-04-24
advocating antivirus in linux at first seemed like a silly thing to me too.  why would you do that?  after all, viruses don't work in linux.  and even if they do, repairs are easily made.

but even though linux can't be infected, it can still be a carrier, and you can cause infections on windows systems.  better to clean the bug in your linux box than to pass it on to your windows computer on your network or your friends/family and try to clean it then.

---

### Post by starscalling on 2006-04-24
~_~
yesh
i carry teh virii to infect u
O WAIT
NO
IM NOT INFECTED AT ALL
\O/
*peers*.
seems i actually have to CONTACT u to INFECT u
ZOMFG ITS THAT IRC THING
o wait no not that either ~_~

---

### Post by Nordoelum on 2006-04-24
What about that crossplatformvirus that is out now?

---

### Post by colo on 2006-04-24
It's a proof of concept which has no real impact. It's distributed as a binary blob. If you happen to run executeable from untrusted sources, you've lost anyway. This process is much more conscious than under Windows, since you can not run an executeable without chmodding it +x for yourself. There is no threat, at least not as of now. Just ditch it.

---

### Post by Perfect Storm on 2006-04-24
Howto: AVG - [http://ubuntuforums.org/showthread.php?t=136064](http://ubuntuforums.org/showthread.php?t=136064)

---

### Post by JimS on 2006-04-24
...

Linux can import, store, and export viruses.
IMHO we should kill them, not harbor them.
It is good citizenship.

[COLOR="Red"]JimS[/COLOR]

,,,

---

### Post by lyleogle on 2006-05-07
[QUOTE=MarvinZurcher]When I launch AVG For Linux Workstation I get thios error message.AVG for Linux was not registred, please register it with valid license number. I enter 70FREE-tx-IB-p1-CO1-S139FC-327-9FPB when I installed the program, but it didn't work. Does anybody know what I did wrong? Thank you in advance[/QUOTE]

Marvin,

How did you go about installing on your Linux Box? I downloaded it yesterday and have not tried to install it yet.

Lyle

---

