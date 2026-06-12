---
title: "Error installing Chrome plz help"
date: 2010-07-27
forum: General Help
---

### Post by rushikesh988 on 2010-07-27
hello friends i am getting error in installing google chorme browser ...



I just downloaded it from its site.whenever I try to install it directly it gives this error

"**COULD NOT OPEN CHROME.deb**

the package cmight be currupted or you are not allowed to open the file.check the permissions of the file"





whenever I try to insatll it from command line it gives this errror




rushikesh@Rushikesh-desktop:~$ cd /home/rushikesh/Desktoprushikesh@Rushikesh-desktop:~/Desktop$ sudo  dpkg -i g.deb
[sudo] password for rushikesh: 
dpkg-deb: `g.deb' is not a debian format archive
dpkg: error processing g.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 g.deb
rushikesh@Rushikesh-desktop:~/Desktop$ 









I also abserved that when I try to install any application through Ubuntu Software Centre



It gives this error

**Requires installation of untrusted packages**
The action would require the installation of packages from not authenticated sources.

---

### Post by rushikesh988 on 2010-07-28
anyone???

---

### Post by Smart Viking on 2010-07-28
Have you tried chromium? It's the same thing.

```
sudo apt-get install chromium-browser
```

---

### Post by su-37 on 2010-07-28
> **Smart Viking said:**
> Have you tried chromium? It's the same thing.

```
sudo apt-get install chromium-browser
```

Almost the same. Chromium is the opensourced base without the google branding and tracking i think.

---

### Post by Smart Viking on 2010-07-28
> **su-37 said:**
> Almost the same. Chromium is the opensourced base without the google branding and tracking i think.

Yeh i know, the same... only better. :P

---

### Post by rushikesh988 on 2010-07-28
what about that last  error in ubuntu software centre???

---

### Post by rushikesh988 on 2010-07-28
anyonee???

---

