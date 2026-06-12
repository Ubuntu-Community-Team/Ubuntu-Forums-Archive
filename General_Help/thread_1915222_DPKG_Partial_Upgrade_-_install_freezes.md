---
title: "DPKG Partial Upgrade - install freezes"
date: 2012-01-25
forum: General Help
---

### Post by bbrhuft on 2012-01-25
I'm using Ubuntu 10.10. My update manager popped up a few days ago asking me to install several security and software updates. I clicked OK and went about browsing the web. But about 30 minutes later I noticed that the update process was frozen, it got stuck trying to update Dahdi (part of Asterisk VoIP software). I also lost read/write access to my hard drive - I couldn't launch any programs and FF started giving weird warnings about not being able to save to the hard drive - so after waiting a while longer I rebooted (I've 380GB free on my HD).

Now synaptic and update manager are inaccessible, they tell me Dpkg was interrupted and I have to do a "Partial Upgrade" by typing *sudo dpkg --configure -a* in a terminal. But when I do so, it gets stuck at Dahdi and like before my computer locks up. I thought of uninstalling Dahdi, but I can't uninstall or install any software. 

I've seen people report similar problems, but I not confident my issue is identical. So apart from reinstalling my OS, what can do?


[IMG]https://dl.dropbox.com/u/2055577/ScreenShot.jpeg[/IMG]

---

### Post by miasmablk on 2012-01-25
try setting up super user permissions VIA:

```
sudo su passwd
```enter you new password it will ask you for it three time and you will not be able to see what you are typing. after the password is created log into super user accoun VIA:

```
su
```enter your password. then launch synaptic through terminal by typing:

```
synaptic
```remove unwanted package and exit synaptic.

also type exit in terminal

now run 
```
sudo dpkg --configure -a
```

---

### Post by bbrhuft on 2012-01-25
No, it doesn't work. I still can't remove dahdi.

This is what synaptic says:

[I]"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."[/I]

---

### Post by miasmablk on 2012-01-26
try 
```
 sudo dpkg -r dahdi
```
or
```
sudo dpkg -P dahdi
```

all i can think of really...anyone else?

---

### Post by miasmablk on 2012-01-26
check out this thread i think it may be useful. :)


[http://ubuntuforums.org/showthread.php?t=1258365](http://ubuntuforums.org/showthread.php?t=1258365)

---

