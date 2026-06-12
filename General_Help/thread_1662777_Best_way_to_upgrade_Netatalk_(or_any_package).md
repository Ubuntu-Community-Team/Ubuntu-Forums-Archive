---
title: "Best way to upgrade Netatalk (or any package)"
date: 2011-01-08
forum: General Help
---

### Post by jay_cee on 2011-01-08
Hi - 

Shortly after upgrading to Meerkat I discovered that my macbook timemachine backups became unreliable to the point of uselessness. After a bit of googling it appears that Meerkat's version of Netatalk (2.1.2) has some issues that bust timemachine. These issues are supposedly fixed in version 2.1.3. 

So... what is the best way for me to go about upgrading Netatalk past the official Meerkat release version?

The Netatalk project is at version 2.1.5. I could uninstall the Meerkat packages and just try to build Netatalk directly from source. However I'm a little leary about losing all of my existing AFPD filesystem meta-data.

The Natty Narwhal repository appears to have version 2.1.4 which I've read should solve my problem. Is there any way to install the binaries from the Natty repositories? Can I download the source package from the Natty repositories and rebuild the package with Meerkat libraries/dependencies? I know all of this is possible, but I don't know how to do it. I'm hoping there is a wiki somewhere or some clear instructions that someone can point me to.

Thanks for any help - J

---

### Post by jay_cee on 2011-01-08
ok - turned out to be easy. Solution was to download 2.1.4 from the Natty Narwhal repository. It installed cleanly. 

Time Machine is now working perfectly.

---

### Post by furam on 2011-02-24
hey!

would you mind to tell me how you did it? it's driving me nuts... everytime my backup reaches full hdd capacity it get's corrupted... I think newer netatalk versions shoud fix it but I am to noobish to build it from source (I tried but it didn't work). any help would be higly appreciated. thanks in advance!

furam

---

### Post by I&#9829;HTML5 on 2011-02-24
> **furam said:**
> hey!

would you mind to tell me how you did it? it's driving me nuts... everytime my backup reaches full hdd capacity it get's corrupted... I think newer netatalk versions shoud fix it but I am to noobish to build it from source (I tried but it didn't work). any help would be higly appreciated. thanks in advance!

furam

Open up Software Sources (System | Administration | Software Sources), click the "Other Software" tab, click "Add", and enter into the box: ```
deb http://archive.ubuntu.com/ubuntu natty universe
``` Now open Terminal and type ```
sudo apt-get upgrade netatalk
``` You should now have version 2.1.4!

---

### Post by furam on 2011-02-25
thank you, mate! you made my day (and probably saved me a lot of time on the weekend). :)

---

### Post by I&#9829;HTML5 on 2011-02-25
Glad I could help! Happy Ubuntuing

---

### Post by furam on 2011-02-25
thank you again! just tried it and it worked flawlessly... I'm on 2.1.4 now and hoping that my problems are gone... :)

---

