---
title: "resolv.conf missing"
date: 2006-06-05
forum: General Help
---

### Post by mikeymouse on 2006-06-05
Resolv.conf is missing when i try to setup my dialup.
I have created a file as Resolv.conf  how do I get this into the /etc directory?
 I have done this before in other systems but without being able to log in as root and create such things i am a bit (lot) lost.
 All help would be appreciated.
 Thanks mikeymouse

---

### Post by erimar77 on 2006-06-05
you can just use the sudo command instead of logging in as root.  
```
sudo cp /path/to/resolve.conf /etc/resolve.conf
```

---

### Post by mikeymouse on 2006-06-05
sudo cp /path/to/resolve.conf /etc/resolve.conf

Do I have to put other info in path/to?
If i enter above it says i need a destination.
Sorry, I have worked with other linux versions and i guese i just do not understand the sudo thing.
 Is there anyway to just go to root do what must be done?
 All help appreciated.
 thanks mikeymouse

---

### Post by professor_chaos on 2006-06-06
[QUOTE=mikeymouse]sudo cp /path/to/resolve.conf /etc/resolve.conf

Do I have to put other info in path/to?
If i enter above it says i need a destination.
Sorry, I have worked with other linux versions and i guese i just do not understand the sudo thing.
 Is there anyway to just go to root do what must be done?
 All help appreciated.
 thanks mikeymouse[/QUOTE]

[https://wiki.ubuntu.com/RootSudo?action=show&redirect=UsingSudo](https://wiki.ubuntu.com/RootSudo?action=show&redirect=UsingSudo)
the /path/to means the path to your backup that you said you made.
So if your backup is in /home/peter/Resolv.conf   
then type
```
sudo cp /home/peter/Resolv.conf /etc/resolv.conf
```

---

