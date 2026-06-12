---
title: "Firefox 5"
date: 2011-07-03
forum: General Help
---

### Post by ladlers on 2011-07-03
In installing Firefox with sudo apt-get install firefox I don't get Firefox version 5. It seems odd that with Firefox being the main browser included with Ubuntu we don't get the greatest. What is the location of Firefox in Ubuntu, so I can install it with the tar command like on Slackware? Also, anyone know an operand to make tar overwrite files in Ubuntu so I don't have to rm them first, or is this just enhanced security?

---

### Post by Toz on 2011-07-03
Which version of ubuntu are you using? Firefox 5 is available for Natty:```
$ apt-cache policy firefox
firefox:
  Installed: 5.0+build1+nobinonly-0ubuntu0.11.04.2
  Candidate: 5.0+build1+nobinonly-0ubuntu0.11.04.2
  Version table:
 *** 5.0+build1+nobinonly-0ubuntu0.11.04.2 0
        500 http://ca.archive.ubuntu.com/ubuntu/ natty-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu/ natty-security/main i386 Packages
        100 /var/lib/dpkg/status
     4.0+nobinonly-0ubuntu3 0
        500 http://ca.archive.ubuntu.com/ubuntu/ natty/main i386 Packages

```

Make sure you have the natty-updates/main repository enabled in **/etc/apt/sources.list**

---

### Post by Rocket2DMn on 2011-07-03
For me, FF 5 doesn't look like a change, but you can check the version either using the method above, or just going to Help -> About Firefox to see the macro version (5 in this case).

---

### Post by ladlers on 2011-07-03
Sorry, I have 10.10 installed. Thanks for the tip.

---

### Post by Toz on 2011-07-03
See: [http://www.webcoz.com/how-to-install-firefox-5-stable-in-ubuntu-10-10-maverick-and-10-10-lucid-from-ppa/]("http://www.webcoz.com/how-to-install-firefox-5-stable-in-ubuntu-10-10-maverick-and-10-10-lucid-from-ppa/")

---

### Post by ladlers on 2011-07-03
Thank you very much, Toz. I must be in a crabby mood today, but what is the command to remove the repository after Firefox is installed? The problem I have with Firefox is that it cannot be auto updated, because it always breaks the add ons. Thus, upgrading Firefox when doing all other upgrades is undesirable. Again, what is the location of Firefox on the hard drive (there are several) and what is the operand, if any, on the tar command to overwrite files?

---

### Post by Toz on 2011-07-03
> **ladlers said:**
> Thank you very much, Toz. I must be in a crabby mood today, but what is the command to remove the repository after Firefox is installed? The problem I have with Firefox is that it cannot be auto updated, because it always breaks the add ons. Thus, upgrading Firefox when doing all other upgrades is undesirable.
Fire up "Ubuntu Software Centre" and under the Edit Menu, there is a "Software Sources" item. Go to the "Other Software" tab and de-select the Firefox PPA(s). Or from the command line, look for the firefox file in **/etc/apt/sources.list.d** and delete it. However, before you do, understand that you won't be getting any of the security updates that get issued.
> Again, what is the location of Firefox on the hard drive The usual location is **/usr/bin/firefox**> (there are several) and what is the operand, if any, on the tar command to overwrite files?I'm sorry but I don't understand why you are trying to untar and overwrite? If you follow the instructions that I linked to, you won't need the tar file you downloaded.

---

### Post by pqwoerituytrueiwoq on 2011-07-04
for most addons disabling the compatibility check will do just fine
both the "addon compatibility reporter" and the "nightly testers tools" addons can do this
this can also be done from about:config you can Google that one

---

### Post by ladlers on 2011-07-04
Thank you for all your help, particularly Toz. Firefox 5 works perfectly. It even automatically updated to the most recent flash player. Open source is the thing!

---

### Post by lovinglinux on 2011-07-04
See [Firefox 4, 5 & Beyond Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247")

---

