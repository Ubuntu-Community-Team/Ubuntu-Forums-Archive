---
title: "New User facing problem please help!"
date: 2011-09-07
forum: General Help
---

### Post by indiankhan81 on 2011-09-07
Hi. I have just installed ubuntu 11.04 on my desktop but during intallation it said that installer crashed. Although the OS was installed i have been not able to start the update manager & nor can i see any new softwares to install in the software center. Please help me as soon as possible!

---

### Post by Beacon11 on 2011-09-07
> **indiankhan81 said:**
> Although the OS was installed...

If the installer crashed I would doubt that the OS was fully installed. Have you tried reinstalling? Make sure the image you downloaded was valid (check the md5 hash) and check the CD you burned to make sure the CD is valid (it's a menu option on the CD on boot).

---

### Post by nipunshakya on 2011-09-07
> **indiankhan81 said:**
> Hi. I have just installed ubuntu 11.04 on my desktop but during intallation it said that installer crashed. Although the OS was installed i have been not able to start the update manager & nor can i see any new softwares to install in the software center. Please help me as soon as possible!


Though i have read it somewhere...but i hope it works for you too(haven't personally tried myself).....give it a shot...



How to fix this problem:
1. Open terminal

2. Enter the following commands one by one:
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

3. Done!.....now try running your update manager...should work fine.....



goodluck with your fixing....

Regards,WinuxUser:p

---

### Post by oldos2er on 2011-09-07
```
sudo rm /var/lib/apt/lists/* -vf

sudo apt-get update
```

---

### Post by nipunshakya on 2011-09-07
and welcome to the forum Mr. India....:):)

---

### Post by Zephonim on 2011-09-07
You can try this in terminal.

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

If that does not work you can try a reinstall like Beacon stated after checking the disc.

---

### Post by Beacon11 on 2011-09-07
> **Zephonim said:**
> sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

... you three do know that you all proposed the same solution, right?

---

