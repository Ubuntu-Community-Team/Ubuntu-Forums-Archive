---
title: "GUI Messup"
date: 2011-05-01
forum: General Help
---

### Post by BoozeWooz on 2011-05-01
Hello,

I'm encountering GUI messups on specific programs such as:
1. libreoffice
2. iceweasel / firefox and all other variants..
See screenshots:

Other programs, such as abiword, chromium browser, synaptic, midori etc don't seem to be affected. This happened after an 'apt-get upgrade'.

Does someone know what this is caused by? (I suspect a broken gtk+ lib or something, but I dont know for sure).

OS:
AntiX 8.5

lsb_release info:
Distributor ID:	Debian
Description:	Debian GNU/Linux testing (wheezy)
Release:	testing
Codename:	wheezy

Regards,
Boozewooz

---

### Post by techunit on 2011-05-01
What OS? You have the thread marked as other OS so that leaves me in a complicated possition. If you are in Unity Ubuntu 11.04 hit alt-f2 and type in unity --reset

That will reset the settings and likely get things working however rather than mention Firefox immediately you mention Ice weasle which makes me wonder if your not using Debian.

Am sure with some more information we can help.

---

### Post by BoozeWooz on 2011-05-01
> **techunit said:**
> What OS? You have the thread marked as other OS so that leaves me in a complicated possition. If you are in Unity Ubuntu 11.04 hit alt-f2 and type in unity --reset

That will reset the settings and likely get things working however rather than mention Firefox immediately you mention Ice weasle which makes me wonder if your not using Debian.

Am sure with some more information we can help.
Thanks for the fast reply. I'm using antix 8.5,

Distributor ID:	Debian
Description:	Debian GNU/Linux testing (wheezy)
Release:	testing
Codename:	wheezy

Regards,
boozewooz

---

### Post by keithpeter on 2011-05-01
> **BoozeWooz said:**
> Thanks for the fast reply. I'm using antix 8.5,

Distributor ID:	Debian
Description:	Debian GNU/Linux testing (wheezy)
Release:	testing
Codename:	wheezy

Regards,
boozewooz

Hello boozewooz

[http://antix.freeforums.org/antix-m8-5-marek-edelman-f40.html](http://antix.freeforums.org/antix-m8-5-marek-edelman-f40.html)

Looks like quite a few issues after recent updates. The wonderfully named anticapitalista who maintains Antix hangs out on the antix forums and he has helpers who reply to questions quickly.

---

### Post by BoozeWooz on 2011-05-02
problem was resolved with 'apt-get dist-upgrade'. thanks all!
regards,
boozewooz

---

