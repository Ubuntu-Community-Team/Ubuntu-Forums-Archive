---
title: "Unity with minimize on click ppa"
date: 2012-05-08
forum: General Help
---

### Post by Rapture1781 on 2012-05-08
Hi!!

```
sudo add-apt-repository ppa:ojno/unity-minimize-on-click
sudo apt-get update
sudo apt-get upgrade
```
Ubuntu 12.04.

Today I have updated to unity 5.12 and now I can't minimize app with click to icon in laucher...

Someone can help me?

The repository is correctly in my system... 

Thank you...

---

### Post by Enigmapond on 2012-05-08
This thread has the PPA I used to build a new Unity with this function. There is also a PPA listed here. I would purge the PPA you have currently and use the one from this thread.
[http://ubuntuforums.org/showthread.php?t=1967822](http://ubuntuforums.org/showthread.php?t=1967822)

---

### Post by philinux on 2012-05-08
> **Rapture1781 said:**
> Hi!!

```
sudo add-apt-repository ppa:ojno/unity-minimize-on-click
sudo apt-get update
sudo apt-get upgrade
```
Ubuntu 12.04.

Today I have updated to unity 5.12 and now I can't minimize app with click to icon in laucher...

Someone can help me?

The repository is correctly in my system... 

Thank you...

What does this show.

```
apt-cache policy unity
```

I suspect the ppa is an older version of unity and would need a rebuild.

Or you can select the version you want from synaptic.

[edit] yep older version. [https://launchpad.net/~ojno/+archive/unity-minimize-on-click](https://launchpad.net/~ojno/+archive/unity-minimize-on-click)

---

### Post by Rapture1781 on 2012-05-08
```
alex@scuotivento:~$ apt-cache policy unity
unity:
  Installato: 5.12-0ubuntu1
  Candidato:  5.12-0ubuntu1
  Tabella versione:
 *** 5.12-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ precise-updates/main i386 Packages
        100 /var/lib/dpkg/status
     5.10.0-0ubuntu6+ojno2 0
        500 http://ppa.launchpad.net/ojno/unity-minimize-on-click/ubuntu/ precise/main i386 Packages
     5.10.0-0ubuntu6 0
        500 http://archive.ubuntu.com/ubuntu/ precise/main i386 Packages
```

So what have I to do? I don't understand...

Thank you at all... for help me!! =)


> **Enigmapond said:**
> This thread has the PPA I used to build a new Unity with this function. There is also a PPA listed here. I would purge the PPA you have currently and use the one from this thread.
[http://ubuntuforums.org/showthread.php?t=1967822](http://ubuntuforums.org/showthread.php?t=1967822)

But this is a differnt version of unity... mmm I don't know...

---

### Post by Enigmapond on 2012-05-08
You have an older version of Unity. Open terminal and do:
```
sudo apt-add-repository ppa:ikarosdev/unity-revamped
```
```
sudo apt-get update && sudo apt-get upgrade
```

This will give you a current unity build with the max/min feature...also the window dodge will work.

---

### Post by Rapture1781 on 2012-05-09
Ok thank you...

Now it works! :D

---

