---
title: "Configuring Compiz: Where do I go next?"
date: 2006-06-06
forum: General Help
---

### Post by MegaBill on 2006-06-06
Hello all, I have been having trouble getting at some off the very specific configuration settings for compiz, like the window shadow color.  I was able to do this with gset-compiz in a previous install, but I have since removed this program and have been unable to reinstall it and get it working properly (I get a no installation candidate error when doing a sudo apt-get install gset-compiz).  Does anyone know a way to configure compiz very specifically other than gconf-settings (not specific enough) and gset-compiz?  Or if anyone knows how to install gset-compiz that would be good also.  Thanks!

---

### Post by 23meg on 2006-06-06
Which repos do you have in your sources.list? gset-compiz should be available for installing.

---

### Post by givré on 2006-06-06
Did you try this [https://wiki.ubuntu.com/CompositeManager](https://wiki.ubuntu.com/CompositeManager)
There is everything you need there

---

### Post by gwpritch on 2006-06-06
Which repos is required for the latest compiz? I also don't have gset-compiz and some of the plugins don't seem to be loaded.

---

### Post by givré on 2006-06-06
[QUOTE=gwpritch]Which repos is required for the latest compiz? I also don't have gset-compiz and some of the plugins don't seem to be loaded.[/QUOTE]
[https://wiki.ubuntu.com/CompositeManager](https://wiki.ubuntu.com/CompositeManager) :wink:

---

### Post by gwpritch on 2006-06-06
missed the link on fast read-through

---

### Post by gwpritch on 2006-06-06
missed the link on fast read-through

---

### Post by matrooswolf on 2006-06-06
the basic thread is: 

[http://www.ubuntuforums.org/showthread.php?t=148351](http://www.ubuntuforums.org/showthread.php?t=148351)

you need to install the quinnstorm repositories

> Installing the latest compiz with all of the new goodies.

    [http://compiz.ed3n.com/viewtopic.php?id=2](http://compiz.ed3n.com/viewtopic.php?id=2)

you can access the different plugins with gconf-editor/apps/compiz

have fun!

---

### Post by MegaBill on 2006-06-06
Very nice, I'll try that out.  I figured it had something to do with the compiz version I was using...

---

### Post by MegaBill on 2006-06-07
Wow, thanks!  Everything works perfectly!  It took some uninstalling and reinstalling, but ultimately I have everything working the way it should, and better than I expected!  Thanks guys!

---

### Post by JerMe on 2006-08-12
To anyone searching for gset-compiz and getting this error, pay a visit to Quinn's site ([http://www.beerorkid.com/compiz/)](http://www.beerorkid.com/compiz/)), which will have information for his latest Xgl/Compiz repositories.  Apparently he either updated or changed repositories, so searching for gset-compiz on the old repositories will throw the "no installation candidate" error.

---

