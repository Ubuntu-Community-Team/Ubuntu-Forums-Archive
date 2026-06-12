---
title: "PATH Variable No Longer Includes /usr/games and /etc/environment is ignored.."
date: 2011-01-13
forum: General Help
---

### Post by manustays on 2011-01-13
Dear All

I use Ubuntu 10.10. Just a few days back most of my games except a few built-in ones stopped working and WarZone2010 was no longer in the menu although it was still installed. So, I checked PATH variable with following result:

echo $PATH
/usr/local/bin:/usr/bin:/bin

The file /etc/environment contains:
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"

The only configuration file in my home dir that could override PATH variable is .bashrc which does not include any reference to PATH.

I have also searched my home dir and /etc/ dir for all files containing "/usr/local/bin:/usr/bin:/bin" but that didnt help!

How should I check which configuration file is overriding my /etc/environment settings?

Please help!!

---

### Post by lithopsian on 2011-01-13
It could be many many things.  Maybe you need to do a fairly wide-ranging search through scripts on your machine for any that reference PATH.  You could also try booting to a console and see what your path is there, to give you an idea where it might be getting set badly.  As a workaround, you could try resetting it in bashrc to something usable.

---

### Post by manustays on 2011-01-23
thanks lithopsian! I guess I'll have to resort to setting it manually in bashrc :)

---

