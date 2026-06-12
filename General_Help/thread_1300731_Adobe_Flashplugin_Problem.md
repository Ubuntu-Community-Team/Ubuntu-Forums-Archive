---
title: "Adobe Flashplugin Problem"
date: 2009-10-25
forum: General Help
---

### Post by lindsay7 on 2009-10-25
Ijkeep getting this message when I open Synaptic Package manager and when I try to update. How do I fix this.


```
The package 'adobe-flashplugin' is in an inconsistent state and needs to be reinstalled, but no archive can be found for it. Please reinstall the package manually or remove it from the system.
```

```
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
```

---

### Post by madinc on 2009-10-25
have you tried to remove and install it back?

---

### Post by gnuisancev3 on 2009-10-25
yeah, try this:

sudo apt-get --purge flashplugin-nonfree

sudo rm /var/cache/apt/archives/*.deb

sudo apt-get install flashplugin-nonfree

---

### Post by lindsay7 on 2009-10-25
This is what I get back,

```
:~$ sudo apt-get --purge flashplugin-nonfree
E: Invalid operation flashplugin-nonfree
 


```

---

### Post by gdonwallace on 2009-10-25
Try doing it through Synaptic Packager Manager.  Do a search for Flash, mark them for complete removal, and when thats done mark them for install.  See if that will fix the problem.

---

### Post by gnuisancev3 on 2009-10-25
> **lindsay7 said:**
> This is what I get back,

```
:~$ sudo apt-get --purge flashplugin-nonfree
E: Invalid operation flashplugin-nonfree
 


```

Excuse me it should've been

```

apt-get --purge remove flashplugin-nonfree 

```

---

### Post by lovinglinux on 2009-10-25
The package adobe-flashplugin has been dropped in Karmic and perhaps in Jaunty too, so the recommended package is flashplugin-nonfree. 

I recommend this:

```
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
```

---

### Post by lindsay7 on 2009-10-25
This is what I am still getting,

```
:~$ sudo apt-get remove swfdec-mozilla
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.

``` 



and Snynaptic still does not work.  I get the same error message.

---

### Post by lindsay7 on 2009-10-25
This is the result from synaptic[ATTACH]133137[/ATTACH]

---

### Post by Biafra on 2009-10-26
Please check this thread.

[http://ubuntuforums.org/archive/index.php/t-1285455.html](http://ubuntuforums.org/archive/index.php/t-1285455.html)

It worked for me - with the same problem.

---

