---
title: "amarok 1.4.0 beta"
date: 2006-04-26
forum: General Help
---

### Post by adamkane on 2006-04-26
amaroK 1.4.0 beta is now available for Breezy:
[http://amarok.kde.org/amarokwiki/index.php/1.4_for_Kubuntu_5.10]("http://amarok.kde.org/amarokwiki/index.php/1.4_for_Kubuntu_5.10")

You can add the czessi repository by adding this line to your sources.list:

> 
deb [http://archive.czessi.net/]("http://archive.czessi.net/") breezy stable stable-updates testing testing-updates
 
Add the czessi gpg key:

```

cd ~/Desktop 
wget http://www.czessi.net/kczessi.gpg 
sudo apt-key add kczessi.gpg 
sudo apt-get update

``` 
Remove libvisual before you install this version of amarok. Otherwise you'll end up with dependency problems:

```

sudo apt-get remove libvisual

```

---

