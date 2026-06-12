---
title: "Can I use Ubuntu Tweak Package Cleaner?"
date: 2010-06-28
forum: General Help
---

### Post by tony123456 on 2010-06-28
I used Ubuntu Tweak Package Cleaner for twice, but the 3rd time I was about to use that function after I removed Audacious, there are more packages like brasero (CD/DVD apllication for Gnome), smartdimmer (Change LCD brightness on Gforce card) showed in the cleaning list, and I don't think these packages depend on or relate to Audacious. So Can I simply clean them? And there are "Clean Cache", "Clean Config", "Clean Kernel" buttons on the right, can I click them and clean?

---

### Post by philinux on 2010-06-28
> **tony123456 said:**
> I used Ubuntu Tweak Package Cleaner for twice, but the 3rd time I was about to use that function after I removed Audacious, there are more packages like brasero (CD/DVD apllication for Gnome), smartdimmer (Change LCD brightness on Gforce card) showed in the cleaning list, and I don't think these packages depend on or relate to Audacious. So Can I simply clean them? And there are "Clean Cache", "Clean Config", "Clean Kernel" buttons on the right, can I click them and clean?

Personally I dont like these cleaners. If I want to remove a package I use synaptic or cli. See man apt-get

```
sudo apt-get purge package

sudo apt-get autoremove
```

---

### Post by tony123456 on 2010-06-28
> **philinux said:**
> Personally I dont like these cleaners. If I want to remove a package I use synaptic or cli. See man apt-get

```
sudo apt-get purge package

sudo apt-get autoremove
```
I tried you method after I've chosen the clean options in the Ubuntu Tweak:
```
tony@tony-laptop:~$ sudo apt-get purge package
[sudo] password for tony: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package package
tony@tony-laptop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Is this normal?

---

### Post by philinux on 2010-06-28
> **tony123456 said:**
> I tried you method after I've chosen the clean options in the Ubuntu Tweak:
```
tony@tony-laptop:~$ sudo apt-get purge **[COLOR="Red"]package[/COLOR]**
[sudo] password for tony: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package **[COLOR="Red"]package[/COLOR]**
tony@tony-laptop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Is this normal?

Errrr.. FacePalm !

sudo apt-get purge (package) subsitute for the package to be reomved.

e.g. ```
sudo apt-get purge audacious

```

---

### Post by tony123456 on 2010-06-30
[[COLOR=#D40000]****[/COLOR]]("http://ubuntuforums.org/member.php?u=353083")Thank you, philinux, I know what to do next time.
[[COLOR=#D40000]****[/COLOR]]("http://ubuntuforums.org/member.php?u=353083")

---

