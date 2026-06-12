---
title: "Root in chinese!"
date: 2011-12-23
forum: General Help
---

### Post by Neraste on 2011-12-23
Hello everyone

I have Ubuntu 11.10 on my EeePC 1215B for days and I have some troubles when I use root privileges. My all system is in French, but my root is (partially) in Chinese...

Let's see, when I want to install something (by instance, *p7zip*), I can read:
> root@Hatsune:~# apt-get install p7zip
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
&#19979;&#21015;&#12304;&#26032;&#12305;&#36719;&#20214;&#21253;&#23558;&#34987;&#23433;&#35013;&#65306;
  p7zip
&#21319;&#32423;&#20102; 0 &#20010;&#36719;&#20214;&#21253;&#65292;&#26032;&#23433;&#35013;&#20102; 1 &#20010;&#36719;&#20214;&#21253;&#65292;&#35201;&#21368;&#36733; 0 &#20010;&#36719;&#20214;&#21253;&#65292;&#26377; 104 &#20010;&#36719;&#20214;&#21253;&#26410;&#34987;&#21319;&#32423;&#12290;
&#38656;&#35201;&#19979;&#36733; 374 kB &#30340;&#36719;&#20214;&#21253;&#12290;
&#35299;&#21387;&#32553;&#21518;&#20250;&#28040;&#32791;&#25481; 1 147 kB &#30340;&#39069;&#22806;&#31354;&#38388;&#12290;
&#33719;&#21462;&#65306;1 [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) oneiric/universe p7zip amd64 9.20.1~dfsg.1-2 [374 kB]
&#19979;&#36733; 374 kB&#65292;&#32791;&#26102; 3s (116 kB/s) 
&#36873;&#20013;&#20102;&#26366;&#34987;&#21462;&#28040;&#36873;&#25321;&#30340;&#36719;&#20214;&#21253; p7zip&#12290;
(&#27491;&#22312;&#35835;&#21462;&#25968;&#25454;&#24211; ... &#31995;&#32479;&#24403;&#21069;&#20849;&#23433;&#35013;&#26377; 173383 &#20010;&#25991;&#20214;&#21644;&#30446;&#24405;&#12290;)
&#27491;&#22312;&#35299;&#21387;&#32553; p7zip (&#20174; .../p7zip_9.20.1~dfsg.1-2_amd64.deb) ...
&#27491;&#22312;&#22788;&#29702;&#29992;&#20110; man-db &#30340;&#35302;&#21457;&#22120;...
&#27491;&#22312;&#35774;&#32622; p7zip (9.20.1~dfsg.1-2) ...That's a little bit... Confusing, isn't it?

That is not I dislike Chinese, but I can't read it, you know.

Actually, Chinese seems to be a default language on Ubuntu 11.10 that appears on the language control panel. But when I try to supress it (through *Instal/Delete Languages*), I am told no Chinese language pack is installed...

One day, accidently, I swhitched system language to Chinese. I have recovered from it, but since, when I use root privileges in terminal, I read Chinese instead of French.

I have searched on the Internet and on this forum, but no one seems to have that problem.

Does anyone have a suggestion?
Thank you a lot for your help!

---

### Post by plucky on 2011-12-23
This is what google translate says ```
The following NEW packages will be installed:
p7zip
0 packages upgraded, 1 newly installed packages, 0 to remove the package, **104 packages not upgraded**.
Need to download the 374 kB of the package.
After unpacking consumed 1 147 kB of additional space.
Get: 1 http://fr.archive.ubuntu.com/ubuntu/ oneiric / universe p7zip amd64 9.20.1 ~ dfsg.1-2 [374 kB]
Download 374 kB, time-consuming 3s (116 kB / s)
Selecting previously deselected package p7zip.
(Reading database ... system currently installed 173383 files and directories.)
Unpacking p7zip (from .../p7zip_9.20.1 ~ dfsg.1-2_amd64.deb) ...
Are dealing with triggers for man-db ...
Is set p7zip (9.20.1 ~ dfsg.1-2) ...
```

Note the 104 packages that have not been updated.

Have you tried running ```
sudo apt-get update && sudo apt-get upgrade
``` from a terminal?

Good Luck

---

### Post by WorMzy on 2011-12-23
Odd.

Can you get a root shell:
```
sudo -i
```
then run
```
locale
```

and post the output here.

---

### Post by Neraste on 2012-01-01
Here I am! Happy new year for everyone!

Thank you for your answer, **WorMzy**. Here is the result of *locale* command in root mode:

> LANG=fr_FR.UTF-8
LANGUAGE=zh_CN:fr:en
LC_CTYPE=**zh_CN.UTF-8**
LC_NUMERIC="fr_FR.UTF-8"
LC_TIME="fr_FR.UTF-8"
LC_COLLATE=**zh_CN.UTF-8**
LC_MONETARY="fr_FR.UTF-8"
LC_MESSAGES=**zh_CN.UTF-8**
LC_PAPER="fr_FR.UTF-8"
LC_NAME="fr_FR.UTF-8"
LC_ADRESS="fr_FR.UTF-8"
LC_TELEPHONE="fr_FR.UTF-8"
LC_MEASUREMENT="fr_FR.UTF-8"
LS_IDENTIFICATION="fr_FR.UTF-8"
LS_ALL=It seems that several elements are in Chinese. How can I fix this?

**plucky**, I will perform an upgrade as soon as I can.

---

### Post by WorMzy on 2012-01-01
That all depends on where they're being set. I'm not sure where Ubuntu keeps it's environment variables these days, but check /etc/environment, /etc/profile, any files in /etc/profile.d (particularly locale.sh, if it exists), and /etc/bash.bashrc

Also check root's home folder for any mention of zh_CN:

```
sudo grep -iR "zh_CN" /root
```

Note that if you need to edit any of these files, you'll need to do it as root.

e.g.

```
gksudo gedit /etc/environment
```

---

### Post by rsvancara on 2012-01-01
How else are Chinese hackers able to take over your system....geesh.

---

### Post by Neraste on 2012-01-08
Thank you, **WorMzy** ! /etc/environment was the place to look after. Here is what it was looking like:
> PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANGUAGE="zh_CNfr:en"
LC_MESSAGES="zh_CN.UTF-8"
LC_CTYPE="zh_CN.UTF-8"
LC_COLLATE="zh_CN.UTF-8"
I have modified the parameters and my root is in French now, as expected.

By the way, is there an /etc/environment equivalent for standard users?

Thanks you and have a nice day.

---

### Post by WorMzy on 2012-01-08
Again, I'm not sure about Ubuntu, but try putting them in ~/.profile, and if that doesn't work, try in ~/.bash_profile

---

