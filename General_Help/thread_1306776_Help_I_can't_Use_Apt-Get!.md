---
title: "Help I can't Use Apt-Get!"
date: 2009-10-30
forum: General Help
---

### Post by kh1116 on 2009-10-30
Trying to update my system, this is what I'm getting. I have no idea whats wrong with it.
```
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
```

---

### Post by SlugSlug on 2009-10-30
> **kh1116 said:**
> Trying to update my system, this is what I'm getting. I have no idea whats wrong with it.
```
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
```


whats the output of 
```
sudo apt-get update
```

---

### Post by kh1116 on 2009-10-31
sudo apt-get update works how its supposed to, however apt-get upgrade i get
```
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.

```

---

### Post by coffeecat on 2009-10-31
I think I remember reading somewhere that the adobe-flashplugin package has been deprecated in favour of flashplugin-nonfree. Certainly at one time there was a choice of either. Try uninstalling adobe-flashplugin and then installing flashplugin-nonfree.

In Karmic you install flashplugin-installer and flashplugin-nonfree is described as a "transitional package that can safely be removed after you installed flashplugin-installer", so if flashplugin-installer is available in Jaunty it might be better to go with that.

---

### Post by liquidbee on 2009-10-31
Did you installed it from the .deb file, downloaded from Adobe website ?

```
sudo dpkg -r adobe-flashplugin
wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb
sudo dpkg -i install_flash_player_10_linux.deb
```

---

### Post by kh1116 on 2009-10-31
Yeah, I figured everything out now. I was unaware that there was a different option than adobe-flashplugin. I've been having some problems so I definitely need to try that out. Thanks everyone

---

