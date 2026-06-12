---
title: "Can not play videos due to &quot;missing plugin&quot;."
date: 2012-04-10
forum: General Help
---

### Post by Wasteblade on 2012-04-10
Hi, I've had Ubuntu for a couple months now, so having switched from Windows 7, I still haven't figured out a lot of things. 
     I've recently upgraded Ubuntu from 11.10 to 12.04 and noticed that a few options have changed. I've also noticed that my computer doesn't play videos anymore. Youtube videos do work, but videos that are embedded on certain sites will not play, stating that I am missing a plug-in. I am absolutely lost.
     I Googled the problem and the suggestions were to disable plug-ins such as VLC Media player and other plug-ins to in a trial and error way, but nothing has changed. I have also installed Adobe Flash player, but yet again have had no luck in being able to watch videos. 
     If anyone has any suggestions, it would be extremely appreciated. I figured that if I won't be able to figure out a solution, I'll transfer my important files to an external hard drive and just re-install 11.10 and stick with that without upgrading from it.
     Thanks in advance for any response. Sorry if I didn't put my thread in the appropriate category, I'm as new to this forum as I am to Ubuntu.

---

### Post by josephmills on 2012-04-10
try this 
open terminal 
enter 
```
sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

then 


```
  sudo apt-get install app-install-data-medibuntu apport-hooks-medibuntu


```

then 

```
sudo apt-get --yes install ubuntu-restricted-extras
```

Let us know how it goes thanks

---

### Post by philinux on 2012-04-10
> **Wasteblade said:**
> Hi, I've had Ubuntu for a couple months now, so having switched from Windows 7, I still haven't figured out a lot of things. 
     I've recently upgraded Ubuntu from 11.10 to 12.04 and noticed that a few options have changed. I've also noticed that my computer doesn't play videos anymore. Youtube videos do work, but videos that are embedded on certain sites will not play, stating that I am missing a plug-in. I am absolutely lost.
     I Googled the problem and the suggestions were to disable plug-ins such as VLC Media player and other plug-ins to in a trial and error way, but nothing has changed. I have also installed Adobe Flash player, but yet again have had no luck in being able to watch videos. 
     If anyone has any suggestions, it would be extremely appreciated. I figured that if I won't be able to figure out a solution, I'll transfer my important files to an external hard drive and just re-install 11.10 and stick with that without upgrading from it.
     Thanks in advance for any response. Sorry if I didn't put my thread in the appropriate category, I'm as new to this forum as I am to Ubuntu.


Use the Mozilla addon flashaid.

 [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by Wasteblade on 2012-04-11
Hi again,

I followed to procedure that josephmills had suggested, but no luck, it still wasn't working. However, I tried Philinux's suggested and videos are working on both Firefox and Chrome. 

Thanks so much for the help.

---

