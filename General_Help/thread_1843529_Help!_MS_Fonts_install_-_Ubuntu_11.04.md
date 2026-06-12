---
title: "Help! MS Fonts install - Ubuntu 11.04"
date: 2011-09-13
forum: General Help
---

### Post by ernestj on 2011-09-13
I tried to install MSCOREFONTS and a message said the the package was not installed because I did not agree to terms? How can I get these fonts on my system?
Thanks,
ernie

---

### Post by Vaphell on 2011-09-13
in terminal
```
sudo apt-get install msttcorefonts
```

after downloading it should present you with a window in text mode with EULA and you have to confirm. Change focus with tab.

---

### Post by ernestj on 2011-09-13
Thank you. Did what you suggested, but it did not ask to confirm with EULA. I still can not find the fonts. Am I not looking for the right name? Times Roman?

---

### Post by howefield on 2011-09-13
Better to try the correct package name

```
sudo apt-get install ttf-mscorefonts-installer
```

---

### Post by Vaphell on 2011-09-13
hm, maybe something has changed since 10.04 - i ran that command and it promted me for confirmation. Oh well.

---

### Post by howefield on 2011-09-13
The change in package name came in with the 10.04 release.

---

### Post by Vaphell on 2011-09-13
yup, just checked the apt-get output - it announced that it goes with ttf-mscorefonts-installer instead.

---

### Post by ernestj on 2011-09-14
I got it to work. Originally, I installed mscorefonts though the Ubuntu software center. I somehow passed the "agree to terms of EULA" and the fonts did not install. The software center was showing that the fonts were installed, but they were not. I inputted the command that Vaphell listed above, but the terminal said the fonts were already installed. I uninstalled the fonts from Ubuntu software center and tried the command again. 
"sudo apt-get install msttcorefonts"


It worked!!

Thank you!

---

