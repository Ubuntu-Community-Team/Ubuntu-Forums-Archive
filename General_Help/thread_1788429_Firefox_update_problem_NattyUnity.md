---
title: "Firefox update problem: Natty/Unity"
date: 2011-06-22
forum: General Help
---

### Post by thenudehamster on 2011-06-22
I thought I was beginning to get to grips with Ubuntu until this came along, and it's driving me MAD! 

On one - and only one, of my four Natty equipped machines, I cannot get Firefox to upgrade beyond 3.5.5 - or at least, it won't launch any later version. I have installed all the required updates and upgrades and both the Unity Update Manager and Synaptic show that 5.0 is installed, but whenever I try to launch it I get 3.5.5. Were I in Windows, I'd know where to look for the application files, delete them and reinstall, but I I'm damned if I know where they are in Linux. (You might by now guess that I'm a user not a code-level programmer; I try, but this is beyond my level of knowledge.)

What is preventing the current version from launching? And what should I do to deal with it?

---

### Post by mike555 on 2011-06-22
Put in the Firefox PPA , then it will update automatically ....... 
sudo add-apt-repository ppa:mozillateam/firefox-next

---

### Post by lovinglinux on 2011-06-22
> **mike555 said:**
> Put in the Firefox PPA , then it will update automatically ....... 
sudo add-apt-repository ppa:mozillateam/firefox-next

There is no need for such ppa on Natty. The OP already have FF 5.0, but 3.5 is still showing.

Try this on a terminal:

```
sudo apt-get remove firefox-3.5
sudo apt-get remove firefox-3.6
sudo apt-get remove firefox-4.0
sudo apt-get update
sudo apt-get install --reinstall firefox
```

---

### Post by thenudehamster on 2011-06-25
This problem is now solved, thanks to advice from 'lovinglinux' here: [  http://ubuntuforums.org/showthread.php?t=1790422]("http://ubuntuforums.org/ubuntuforums.0rg/showthread.php?t=1790422") 

My thanks again.

---

### Post by lovinglinux on 2011-06-25
> **thenudehamster said:**
> This problem is now solved, thanks to advice from 'lovinglinux' here: [  http://ubuntuforums.org/showthread.php?t=1790422]("http://ubuntuforums.org/ubuntuforums.0rg/showthread.php?t=1790422") 

My thanks again.

You are welcome.

---

