---
title: "Ubuntu file error. please help. all booting freez."
date: 2011-02-15
forum: General Help
---

### Post by adeee on 2011-02-15
Guys i just login on ubuntu 3 hours before. and update notification appears.
i just update via update manager.
after that when i try to open any file this error appears.
i reboot computer. and on playmouth screen computer gone freez and not login screen appears.
in Alt+f1 mode. i successfully login. when i try to open any thing there still this massage appear.
How can i resolve it?

Can i remove the last updates? or remove file?

adeee@adeee:~$ sudo synaptic
synaptic: symbol lookup error: /usr/lib/libgdk-x11-2.0.so.0: undefined
symbol:
adeee@adeee:~$ iceape
/usr/lib/iceape/iceape-bin: symbol lookup error:
/usr/lib/libgdk-x11-2.0.so.0: undefined symbol: g_malloc_n

Help me please..........
Recently am on windows xp. and already too much time wasted to solve via googling.. so help please.

---

### Post by sikander3786 on 2011-02-15
Please post the output of these commands.

```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install -f
sudo dpkg --configure -a
```

While posting, click the # icon in post menu and paste your text in between the generated [code] tags.

---

### Post by adeee on 2011-02-15
> **sikander3786 said:**
> Please post the output of these commands.

```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install -f
sudo dpkg --configure -a
```While posting, click the # icon in post menu and paste your text in between the generated [code] tags.



Ok here is the results.
For sudo apt-get update
[ATTACH]183551[/ATTACH]

in [COLOR=DarkRed]uper side of pic[/COLOR] it shows that internet is not connected but its connect.

Second result.
Show the [COLOR=Red]sudo apt-get upgrade[/COLOR]
third [COLOR=Red]sudo apt-get install -f[/COLOR]

and last one is [COLOR=Red]sudo dpkg --configure -a[/COLOR]
[ATTACH]183552[/ATTACH]

---

### Post by sikander3786 on 2011-02-15
Try,

```
sudo rm /var/lib/apt/lists/* -vf
sudo rm -vf /var/cache/apt/*.bin
```

And then follow the same commands as above.

---

