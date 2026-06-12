---
title: "need root privlages to change files in own home folder"
date: 2011-07-16
forum: General Help
---

### Post by 3rikholmgr3n on 2011-07-16
I'm running ubuntu 64-bit server edition so ill have to use the command line for this. whenever i want to create or change a file in my own home folder, i have to do it as sudo, otherwise i get an error message saying "permission denied". Any help would be appreciated. thanks.

---

### Post by Bucky Ball on 2011-07-16
Welcome. Well, yea. That would be normal. If you are running in a server install you have groups and permissions if you set them up. You possibly haven't yet. ;)

You can load a lightweight desktop environment to help set things up then get rid of it later, xfce for instance with:

```
sudo apt-get install xfce4
```

If you are already familiar with working in the console, then you would assume that being root is the only way you can alter the settings on your computer? That is why it is Linux and not a leaky bucket! lol

---

### Post by BrendanM on 2011-07-16
What user are you logged in as?

$ whoami

Who do the files in your home directory belong to? What do their permissions look like?

$ ls -alh

If you originally created those files using sudo, they will probably belong to the root user. You can change the ownership and permissions of files with chmod and chown: [http://www.ghacks.net/2011/02/18/linux-101-using-chmod-and-chown/](http://www.ghacks.net/2011/02/18/linux-101-using-chmod-and-chown/)

Be aware that if you are in a server environment with multiple users, changing owner/permissions may have important security implications.

---

### Post by bodhi.zazen on 2011-07-16
> **Bucky Ball said:**
> Welcome. Well, yea. That would be normal. If you are running in a server install you have groups and permissions if you set them up. You possibly haven't yet. ;)

This is not normal, users should have full permissions in their home directory.

> You can load a lightweight desktop environment to help set things up then get rid of it later, xfce for instance with:

```
sudo apt-get install xfce4
```If you are already familiar with working in the console, then you would assume that being root is the only way you can alter the settings on your computer? That is why it is Linux and not a leaky bucket! lol

No, you do NOT need to install a graphical desktop.

use sudo to chown and chmod the home directory.

```
sudo chown -R user:user /home/user
sudo chmod 770 /home/user
```

---

### Post by Bucky Ball on 2011-07-16
Your messages are humbly received and understood, B. Good luck with it. ;)

---

