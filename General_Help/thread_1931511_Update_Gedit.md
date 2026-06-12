---
title: "Update Gedit"
date: 2012-02-25
forum: General Help
---

### Post by B@sS!A on 2012-02-25
hi guys
i just want to know how to upgrade to the last version of the text editor "Gedit", i want the version 3 i guess (which exsists in ubuntu 12.04)
i already downloaded the last version from the official website, but in the installation it have many dependencies :(
so please give me a method to upgrade to Gedit 3 easily
thanks in advance

---

### Post by baumanno on 2012-02-25
B@sS!A,

well, I'm using 11.10, and, as you can see:
```
$ gedit -V
gedit - Version 3.2.3

```

This suggests that gedit3 is in the repositories, so why not try

```

$ sudo apt-get update
$ sudo apt-get upgrade

```

No offense meant if you already tried this, but it does seem like the simplest solution there is...

---

### Post by B@sS!A on 2012-02-25
> **baumanno said:**
> B@sS!A,

well, I'm using 11.10, and, as you can see:
```
$ gedit -V
gedit - Version 3.2.3

```This suggests that gedit3 is in the repositories, so why not try

```

$ sudo apt-get update
$ sudo apt-get upgrade

```No offense meant if you already tried this, but it does seem like the simplest solution there is...

thank you for the reply, i already tried this, but i've installed all the updates in the repositories but it doesn't contains Gedit 3.2

anyone have the correct repositories link to add so i can update it?

---

### Post by josephmills on 2012-02-25
please open terminal 
then 
```
sudo apt-add-repository ppa:suraia/ppa  
```
then 
```
sudo apt-get update 
```
then 
```
sudo apt-get remove gedit && sudo apt-get install gedit 
```
then 
```
sudo apt-add-repository -r ppa:suraia/ppa 
```
then reboot then 
```
gedit -V 
```
	?? 3.3.4 ??

Hope that this helps

---

### Post by B@sS!A on 2012-02-25
> **josephmills said:**
> please open terminal 
then 
```
sudo apt-add-repository ppa:suraia/ppa  
```then 
```
sudo apt-get update 
```then 
```
sudo apt-get remove gedit && sudo apt-get install gedit 
```then 
```
sudo apt-add-repository -r ppa:suraia/ppa 
```then reboot then 
```
gedit -V 
```    ?? 3.3.4 ??

Hope that this helps


i followed these instructions i can't reboot now because i'm downloading something :)
but i think this is the right method, thank you very much sir, i will repost here if this worked.

---

### Post by B@sS!A on 2012-02-26
after the instructions of [B]josephmills i still get the Version 2.30.4

[/B]

---

### Post by baumanno on 2012-02-26
What Ubuntu-release are you on? Because I remember reading somewhere that Gedit3 is integrated into the Gnome3-release, which in turn means it has dependencies on it.

---

### Post by B@sS!A on 2012-02-26
i'm using Ubuntu 11.04 (natty)

---

### Post by philinux on 2012-02-26
> **B@sS!A said:**
> hi guys
i just want to know how to upgrade to the last version of the text editor "Gedit", i want the version 3 i guess (which exsists in ubuntu 12.04)
i already downloaded the last version from the official website, but in the installation it have many dependencies :(
so please give me a method to upgrade to Gedit 3 easily
thanks in advance

I'm using 11.10

```
apt-cache policy gedit
gedit:
  Installed: 3.2.3-0ubuntu0.1
  Candidate: 3.2.3-0ubuntu0.1
```

And 12.04 gives.

```
apt-cache policy gedit
gedit:
  Installed: 3.3.4-0ubuntu1
  Candidate: 3.3.4-0ubuntu1

```

---

### Post by philinux on 2012-02-26
> **B@sS!A said:**
> i'm using Ubuntu 11.04 (natty)

Ah that explains it then.

---

### Post by baumanno on 2012-02-26
Try [http://www.ubuntuupdates.org/package/gnome_3/natty/main/base/gedit](http://www.ubuntuupdates.org/package/gnome_3/natty/main/base/gedit) and get the .deb-file for your infrastructure (they're currently supplying 3.0.6).
Any luck?

---

### Post by B@sS!A on 2012-02-26
> **baumanno said:**
> Try [http://www.ubuntuupdates.org/package/gnome_3/natty/main/base/gedit](http://www.ubuntuupdates.org/package/gnome_3/natty/main/base/gedit) and get the .deb-file for your infrastructure (they're currently supplying 3.0.6).
Any luck?


thanks, i tried but i got this message ; Dépendance non satisfaite : libpeas-1.0-0 (>= 1.0.0)

---

### Post by B@sS!A on 2012-02-26
i"ve installed libpeas 1.0.0 but i keep have the message

---

### Post by baumanno on 2012-02-26
Try
```
$ sudo apt-get -f install gedit
```

---

### Post by B@sS!A on 2012-02-26
with this command i get the version 2.30.4

---

### Post by Frogs Hair on 2012-02-26
The default version for 11.10 is Gedit 3.2.3 and there is a PPA for a Higher version but they are Gnome 3 Compatible . If you are using a Gnome 2 release you may not be able to install these .

---

### Post by B@sS!A on 2012-02-26
thanks frogs hair, i think i will migrate to gnome 3, the problem i like classical desktop dunno if there's one in gnome 3

---

### Post by Frogs Hair on 2012-02-26
See the link after you upgrade . I would suggest a backup and clean installation for best results . [http://ubuntuforums.org/showthread.php?t=1859960](http://ubuntuforums.org/showthread.php?t=1859960)

---

### Post by philinux on 2012-02-26
> **B@sS!A said:**
> thanks frogs hair, i think i will migrate to gnome 3, the problem i like classical desktop dunno if there's one in gnome 3

You could use xfce.

---

### Post by B@sS!A on 2012-02-26
thank you all, i think i'll find an alternative for Gedit, because i want to keep ubuntu 11.04 and gnome 2

---

