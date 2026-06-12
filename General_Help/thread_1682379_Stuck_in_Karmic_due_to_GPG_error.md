---
title: "Stuck in Karmic due to GPG error"
date: 2011-02-05
forum: General Help
---

### Post by BandeAli on 2011-02-05
Hello I am using a desktop with Karmic (9.10) ubuntu and I had not bother upgrading to 10.04 for a while because I didn't use the computer as much. 

Now I am unable to upgrade at all. Whenever I go into update manager and click on check I get the following error.
> W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release: Unknown error executing gpgv
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) jaunty Release: Unknown error executing gpgv
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release: Unknown error executing gpgv
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) karmic Release: Unknown error executing gpgv
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release: Unknown error executing gpgvHowever I am able to update my packages through the terminal using apt-get in which it warns me that the packages are unauthenticated and allows me to install it anyway. However, update manager doesn't give the option to upgrade my ubuntu version.

---

### Post by oldos2er on 2011-02-05
What happens if you run ```
sudo apt-key update
``` ?

---

### Post by BandeAli on 2011-02-05
I have noticed this before and tried to reinstall libreadline6 but that has not made a difference. 

> gpg: symbol lookup error: /usr/local/lib/libreadline.so.6: undefined symbol: PC
gpg: symbol lookup error: /usr/local/lib/libreadline.so.6: undefined symbol: PC


---

### Post by BandeAli on 2011-02-07
so I am stuck forever? Should I just go ahead and reinstall ubuntu (i really want that to be the last resort)?

---

### Post by wojox on 2011-02-07
Have you tried reinstalling GPG:


```
sudo apt-get install gnupg
```

---

### Post by oldos2er on 2011-02-07
Maybe there's some info here that can help: [http://www.unix.com/ubuntu/123074-cant-update-use-package-manager-gpg-error.html](http://www.unix.com/ubuntu/123074-cant-update-use-package-manager-gpg-error.html)

---

