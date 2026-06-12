---
title: "Help! My Ubuntu installation has broken packages"
date: 2011-06-19
forum: General Help
---

### Post by linuxuser12345 on 2011-06-19
I am trying to install the Chromium browser on my netbook running Ubuntu 11.04, and every time I try to install it, either via the Ubuntu Software Center or Synaptic, the installation always cancels on me because it says I have "broken packages that need to be fixed."

Can someone please help me out here? Thank you! :)

---

### Post by Enigmapond on 2011-06-19
Have you tried going to synaptic and hitting "custom filters"/broken to try to either install or uninstall the broken package?

---

### Post by Joe- on 2011-06-19
Ignore the image: Edit>Fix Broken Packages

---

### Post by knutschr on 2011-06-19
Copy to terminal:
```
sudo dpkg --configure -a  
```

---

### Post by munkeh on 2011-06-19
Hi Linuxuser12345

I have just been having a similar broken package problem as you. I could not find a fix, all the suggested ones did not work, so I done some investigating on my machine and found that the /var/lib/dpkg/status file had about 30 lines corrupted. So what I done as I noticed that next to the status was status-old, in the terminal I backed up status-old

```
 cd /var/lib/dpkg
``````
 sudo cp status-old status-old-backup
```Then I swapped the current 'status' for the old one

```
 sudo mv status-old status
```To test I just typed

```
 sudo apt-get update
```Then everything seemed back to normal.

Please note, on Ubuntu 10.10 I have made this up myself and do not know if it may have dire consequences for others although it seems harmless to little me. So if you are not sure about doing it then please don't. Someone more knowledgeable may suggest something better or say it is okay to do.

I hope you get it sorted one way or another.

---

