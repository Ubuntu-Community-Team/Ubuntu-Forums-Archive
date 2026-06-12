---
title: "Need help with fixing dpkg"
date: 2012-06-22
forum: General Help
---

### Post by rabbidninja on 2012-06-22
I've run a script *(ubuntu-12.04-postinstall.py)* that auto-installs suggested programs all of it worked fine until it tried to install dropbox. It got to 99% and froze for quite a while. So, I closed the terminal out and rebooted. Now when i try and apt-get install command line it spits back out **"E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem".** I do this and eventually am able to install software but then it tries to install dropbox again automatically and still gets stuck at 99%. My question is, how can i get this cleared from dpkg? I really don't want to have to run through hoops every time just to install new software! *(btw this is with lubuntu 12.04 if that matters) (Also, dont want to re-install lubuntu as it was a pain as I had downloaded a horrible copy of the distro! It took me over 15 hours to fix and install)*
Thank you in advance!

---

### Post by jmfal on 2012-06-22
I had problems installing dropbox myself.

If you edit that script  ,  comment out dropbox by putting a "#" at the beginning of the line.

Or you should be able to move that script out of the folder so it doesn't run.

---

### Post by montego95 on 2012-06-25
What about those of us who just tried to install Dropbox from the Ubuntu repositories are stuck at the same place?  I cannot get passed this one bad installation no matter what I've tried.  I've even tried uninstalling dropbox but it won't even do that until this error is cleared.  I'm at a loss.

---

### Post by jmfal on 2012-06-25
Try this link Montego95

[http://askubuntu.com/questions/154671/dropbox-install-stuck-at-99-how-do-i-fix-it](http://askubuntu.com/questions/154671/dropbox-install-stuck-at-99-how-do-i-fix-it)

---

### Post by jmfal on 2012-06-25
I forgot to add  go to fix first then go back to top if you want to installl dropbox ppa

---

### Post by montego95 on 2012-06-25
That fixed it!  Thank you.

---

