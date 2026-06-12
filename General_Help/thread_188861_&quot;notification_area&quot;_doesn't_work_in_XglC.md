---
title: "&quot;notification area&quot; doesn't work in Xgl/Compiz"
date: 2006-06-04
forum: General Help
---

### Post by Marcos.Rufino on 2006-06-04
I'm using Ubuntu Dapper Drake with Xgl and Compiz. 

With Xgl/Compiz I can't use the notification area in Gnome. I can easily include the notification area in Gnome toolbar; the problem is that it doesn't show the running applications it usually shows. 

So, when I use, for instance, amaroK or Azureus their icons don't show up in the notification area.

Does anyone know how I could fix it? Thanks!

---

### Post by testube_babies on 2006-06-04
Are you using the latest versions of XGL/Compiz or the ones included in the Dapper repositories?  When I upgraded to the latest versions, amaroK magically appeared in my notification area.

---

### Post by tUrtleAE86 on 2006-06-05
(Using Gnome) I'm getting the same problem with QuinnStorm's Compiz packages. I can't even get Amarok to load. I'm assuming it's because of the notification area problem.

Gnome programs that use the notification area seem to work just fine.

Any ideas?

---

### Post by fornix on 2006-06-07
I have the same problem. I installed Xgl / Compiz by following the guide in this forum. It works great. Only problem is that programs like amarok dont show up in notification area. Any help will be appreciated.
> Are you using the latest versions of XGL/Compiz or the ones included in the Dapper repositories? When I upgraded to the latest versions, amaroK magically appeared in my notification area.
Can you please tell how you upgraded to latest versions. Thanks in advance

---

### Post by testube_babies on 2006-06-07
```
sudo gedit /etc/apt/sources.list
```

Add this to the bottom of the file and save:

deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main
deb-src [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

Then,
```
wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome
```

Then, follow the directions (starting at step 2) here:
[http://ubuntuforums.org/showthread.php?t=148860](http://ubuntuforums.org/showthread.php?t=148860)

---

