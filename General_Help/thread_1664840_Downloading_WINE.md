---
title: "Downloading WINE"
date: 2011-01-11
forum: General Help
---

### Post by skok0425 on 2011-01-11
Downloaded Wine in Terminal as per directions.  However, seems to be hung up on a Windows EULA window.  Any suggestions or just close and move on?
Thanks.:popcorn:

---

### Post by bodhi.zazen on 2011-01-11
How are you installing wine ?

---

### Post by skok0425 on 2011-01-11
sudo add-apt-repository ppa:ubuntu-wine/ppa

sudo apt-get update

sudo apt-get install wine1.3

---

### Post by bodhi.zazen on 2011-01-11
You will probably need to accept the EULA then. Scroll down and / or try the tab key.

---

### Post by skok0425 on 2011-01-11
Tab worked to let me accept.  Thanks a lot!

---

### Post by bodhi.zazen on 2011-01-11
You are most welcome.

---

### Post by howefield on 2011-01-11
It'll have been the ttf-mscorefonts-installer package which is installed along with Wine and which requires the EULA. Just for info.

---

