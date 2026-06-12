---
title: "Issues logging in after upgrading to 12.04"
date: 2012-04-26
forum: General Help
---

### Post by Rovanion on 2012-04-26
After the upgrade today I'm now faced with an error upon login:

System tray is unavavailable, quitting.

After this I'm left a blue screen and a mouse pointer, that's all.

---

### Post by codingman on 2012-04-26
Can you give some more info? Like what exactly is the error message?

---

### Post by codingman on 2012-04-26
is it like this bug? [https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/959344](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/959344)

---

### Post by Rovanion on 2012-04-26
> **codingman said:**
> Can you give some more info? Like what exactly is the error message?
 
The error is exactly:

System tray is unavailable, quitting.

---

### Post by Rovanion on 2012-04-26
> **codingman said:**
> is it like this bug? [https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/959344](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/959344)

No, but I got a paste of my syslog:[ paste.ubuntu.com/948151]("http://paste.ubuntu.com/948151")

---

### Post by codingman on 2012-04-26
Do you have any other OS's on the computer?

---

### Post by Rovanion on 2012-04-26
> **codingman said:**
> Do you have any other OS's on the computer?
Yes.

---

### Post by codingman on 2012-04-26
There seems to be some errors with Ubuntu not finding important files. I suggest a clean install, did this happen on the first boot?

---

### Post by codingman on 2012-04-26
'Cause if so, there must have been an error when installing Ubuntu.Can you check via your other OS whether the other Ubuntu has all required files?

---

### Post by Rovanion on 2012-04-26
> **codingman said:**
> 'Cause if so, there must have been an error when installing Ubuntu.Can you check via your other OS whether the other Ubuntu has all required files?

I can log into KDE just fine. It's just Unity that crapps out. How do I find these missing files you tell me of?

---

### Post by Rovanion on 2012-04-26
> **codingman said:**
> There seems to be some errors with Ubuntu not finding important files. I suggest a clean install, did this happen on the first boot?

Yes this happened on the first boot after upgrading.

---

### Post by codingman on 2012-04-26
Ohhhhhhhhhhhhhhhhhhhhhhhhh, OK I thought you couldn't boot (It would be highly unlikely because the kernel seems to be working fine). Then do this in terminal 


sudo apt-get install unity

That should work.

---

### Post by codingman on 2012-04-26
If it happened the first time then it means there was a fail in installation.

---

### Post by Rovanion on 2012-04-26
> **codingman said:**
> Ohhhhhhhhhhhhhhhhhhhhhhhhh, OK I thought you couldn't boot (It would be highly unlikely because the kernel seems to be working fine). Then do this in terminal 


sudo apt-get install unity

That should work.

Sadly it does not. It's already installed and up to date the terminal tells me.

---

### Post by codingman on 2012-04-26
Do

sudo apt-get remove unity 

then do the same thing

sudo apt-get install unity

Hope this works!

---

### Post by Rovanion on 2012-04-26
> **codingman said:**
> Do

sudo apt-get remove unity 

then do the same thing

sudo apt-get install unity

Hope this works!

Made no difference.

---

### Post by codingman on 2012-04-26
The only last choice is a fresh install. There must be some to many files lost in the process of installation...sorry #-o for the inconvenience this has caused you.

---

### Post by cryptotheslow on 2012-04-26
You could try executing the command

```
unity --reset
```

That should return unity settings to their defaults.

What version did you upgrade from?

---

### Post by codingman on 2012-04-26
I am an idiot! I totally forgot about that! ](*,)](*,)](*,)](*,)](*,)](*,)](*,)](*,)

---

### Post by 1204 on 2012-04-26
*oops wrong thread -please delete this msg*

---

### Post by jorpiell on 2012-04-27
I've got the same error and I've reinstall unity. It has worked in my case.

---

### Post by Rovanion on 2012-04-27
> **cryptotheslow said:**
> You could try executing the command

```
unity --reset
```That should return unity settings to their defaults.

What version did you upgrade from?

I'm having this issue on two desktops one going trough the whole 12.04 alpha and an other upgraded from 11.10.

This command did not resolve the issue I'm afraid.

---

### Post by Rovanion on 2012-04-27
I just realised that this message: No Systray, Quitting. is a message from Synergy and is just a symptom of the problem and not an error from the actual issue.

---

### Post by techsupport on 2012-04-27
> **Rovanion said:**
> I just realised that this message: No Systray, Quitting. is a message from Synergy and is just a symptom of the problem and not an error from the actual issue.

Fresh install should fix this:

[http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

Just go down the list slowly.

---

### Post by Rovanion on 2012-04-27
> **techsupport said:**
> Fresh install should fix this:

[http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

Just go down the list slowly.

Not necessarily since I keep my home on a separate partition, if it's a config file issue it will persist.

---

