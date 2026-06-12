---
title: "How Install Latest Firefox?"
date: 2011-06-20
forum: General Help
---

### Post by mawil1013 on 2011-06-20
3.6.17 is my current version of Firefox. I went to Firefox download and downloaded version 4.0.1, how do I get it to install?

Running Ubuntu 10.04 LTS.

---

### Post by pqwoerituytrueiwoq on 2011-06-20
**sudo apt-add-repository ppa:mozillateam/firefox-stable**

---

### Post by mawil1013 on 2011-06-20
> **pqwoerituytrueiwoq said:**
> **sudo apt-add-repository ppa:mozillateam/firefox-stable**

Didn't work, I opened Terminal, entered, 
sudo apt-add-repository ppa:mozillateam/firefox-stable

just as it is written above,

it asked for my password, cursor didn't mover nor did it appear that PW entered but I pressed Enter anyway and about 8 lines came up key ring this key ring that.

Restarted and still shows old version.

---

### Post by pqwoerituytrueiwoq on 2011-06-20
sorry, thought you would know to run the update manager after that
don't forget to check for updates
> it asked for my password, cursor didn't mover nor did it appear that PW entered but I pressed Enter anywaysecurity feature that hides password

---

### Post by lovinglinux on 2011-06-21
After installing the ppa, you need to update and upgrade. See [Firefox 4,5 & Beyond Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247")

BTW, Firefox 5 will be released today. It should be available in the *firefox-stable* ppa soon and also in the official repositories.

---

### Post by srisharan on 2011-06-21
Now do;
 sudo apt-get update 
 sudo apt-get upgrade

---

### Post by mawil1013 on 2011-06-21
> **pqwoerituytrueiwoq said:**
> sorry, thought you would know to run the update manager after that
don't forget to check for updates
security feature that hides password

That did it! Your the greatest! :popcorn:

---

