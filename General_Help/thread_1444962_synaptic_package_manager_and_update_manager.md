---
title: "synaptic package manager and update manager"
date: 2010-04-02
forum: General Help
---

### Post by roynoblin on 2010-04-02
when i try to access synaptic package manager and update manager or ububtu software center. the screen will flash and be gone

can any one tell me how to fix this?

---

### Post by jmszr on 2010-04-02
roynoblin,

I had a similar problem and the fix was (copy and paste in terminal):

```
sudo rm /var/cache/apt/*.bin
```

Hope that helps.

---

### Post by roynoblin on 2010-04-02
thanks but that didn't help
i have been all over this forums trying different things and keep getting this
roy@roy-desktop:~$ apt-get update

E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock the list directory

roy@roy-desktop:~$ apt-get upgrade
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

roy@roy-desktop:~$ sudo rm /var/cache/apt/*.bin
[sudo] password for roy: 
roy@roy-desktop:~$ sudo rm /var/cache/apt/*.bin
rm: cannot remove `/var/cache/apt/*.bin': No such file or directory

i am brand new to ubuntu and have no idea what this means. i welcome any and all help

also if i try to access ubuntu software center, i just see the screen flash on then it is gone

---

### Post by jmszr on 2010-04-02
roynoblin,

You need to use sudo:

```
sudo apt-get update
```

Here are a couple of links to an explanation of sudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) and [http://linux.about.com/od/ubuntu_doc/a/ubudg24t4.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg24t4.htm)

---

### Post by CompyTheInsane on 2010-04-02
> **roynoblin said:**
> when i try to access synaptic package manager and update manager or ububtu software center. the screen will flash and be gone

can any one tell me how to fix this?

What output do you get when you try running Synaptic from the terminal?
```

sudo synaptic

```
or Update Manager
```

update-manager

```
Or the Ubuntu Software Center?
```

software-center

```

---

### Post by roynoblin on 2010-04-02
thank you every one.
 i shutdown this PC and went to bed. today when i restarted everything is working.
i have no idea what was wrong or what fixed the problem but i can now access everything and was able to download and run VLC.
:D

---

