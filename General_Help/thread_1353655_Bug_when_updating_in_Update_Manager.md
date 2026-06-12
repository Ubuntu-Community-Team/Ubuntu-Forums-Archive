---
title: "Bug when updating in Update Manager"
date: 2009-12-13
forum: General Help
---

### Post by CiscoPixie on 2009-12-13
Hi guys! I'm quite new to Ubuntu and upgraded recently to Karmic Koala. I went to check for upgrades and i got an error which is attached below. It said something about "unable to lock download directory." Does anyone know what this means?? Thanks in advance :P

---

### Post by deathbyswiftwind on 2009-12-13
Try flushing your apt cache and then restarting. I once had a deb file in the apt cache that didnt correctly install and for some reason apt kept reading it like it was still being installed by one of the package managers. Cleared the cache and all was well.

---

### Post by bumanie on 2009-12-13
You probably have software centre or synaptic open at the same time. Make sure all is closed then try updates again.

---

### Post by CiscoPixie on 2009-12-13
i did this: ash@ash-laptop:~$ sudo apt-get clean
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory
Now i'm at a loss.. i followed the directory and the lock file is of an unknown format. What should the format be?
And i didnt have both open at the same time. just update manager.

---

### Post by tombola on 2010-06-08
I found Randy Jensen's suggestion helpful; open a terminal window and enter the following code to kill any "Synaptic" processes that are running. It worked for me, and I was getting the same error even without any windows open besides Update Manager. 

sudo pkill apt

---

### Post by Oldieone56 on 2010-07-15
Tombola - using  sudo pkill apt worked for me too. Thanks.

---

### Post by Innigo on 2010-07-26
+1 here for me too guys. As soon as I did "sudo pkill apt" the error box disappeared and firefox updates proceeded to install. I wonder where this "download directory" is?  I don't think it's the user's "Downloads".

---

