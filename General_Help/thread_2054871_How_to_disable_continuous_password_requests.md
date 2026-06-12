---
title: "How to disable continuous password requests"
date: 2012-09-08
forum: General Help
---

### Post by LK_gandalf_ on 2012-09-08
Hi all, I use Linux since many years and I'm realizing that I don't want to type in my password every two seconds. It is really annoying and useless in my case, my pc is always at home and I don't have any enemies around here. I don't want to type my password every time I need to install a program and I don't want to use the wallet.
Is there a way to disable this function?
Thanks

---

### Post by jerrrys on 2012-09-08
check it out

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=disable+password&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=disable+password&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by steeldriver on 2012-09-08
The safest way is NOT to disable the password, but to increase the length of the timeout

[https://help.ubuntu.com/community/RootSudoTimeout](https://help.ubuntu.com/community/RootSudoTimeout)

---

### Post by grahammechanical on 2012-09-08
Versions of Ubuntu later than 10.04 have removed the need to enter a password so many times.

On 12.04 I hardly put a password once I have log in. There has been much improvement in this area over the last few years.

Regards.

---

### Post by Epodx64 on 2012-09-08
You could enable the Root account and log in as root instead of user but I'd highly advise against that or I suppose your could elevate your user account to root status.

---

### Post by oldos2er on 2012-09-08
**sudo -i** gives you a persistent root shell. Type **exit** when done.

---

