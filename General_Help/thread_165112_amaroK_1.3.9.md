---
title: "amaroK 1.3.9"
date: 2006-04-24
forum: General Help
---

### Post by adamkane on 2006-04-24
I've already posted this info in the automatiks thread, but this bit of info deserves its own thread I think.

The czessi repository makes amarok v1.3.9 available to breezy users (thanks aysiu).

Repository listing:
[http://www.czessi.net/breezy.php?i18n=en]("http://www.czessi.net/breezy.php?i18n=en")

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

Remove libvisual before you install amarok 1.3.9, otherwise you'll end up with dependency problems:
 ```

 sudo apt-get remove libvisual
 
```

 * If the czessi repository is a bit slow, you can download the amarok deb files here:
 [http://archive.czessi.net/pool/breezy/stable-updates/i386/]("http://archive.czessi.net/pool/breezy/stable-updates/i386/")

---

### Post by aysiu on 2006-04-24
You can also get AmaroK 1.3.9 by upgrading to Dapper.

---

