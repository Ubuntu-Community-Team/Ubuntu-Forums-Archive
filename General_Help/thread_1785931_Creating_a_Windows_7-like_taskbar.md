---
title: "Creating a Windows 7-like taskbar"
date: 2011-06-18
forum: General Help
---

### Post by linuxuser12345 on 2011-06-18
Hey, I LOVE the new taskbar released in Windows 7, and I am trying to figure out if there is something almost identical I can get or assemble for Linux.
Can someone point me in the right direction, if possible?

Thanks! :)

---

### Post by linuxuser12345 on 2011-06-18
I would prefer it to work seamlessly with Kubuntu, but I would also like to see a way to do it with other Linux and Ubuntu types.

---

### Post by linuxuser12345 on 2011-06-19
Can somebody help me?

---

### Post by christopher.wortman on 2011-06-19
Your best bet is KDE not Gnome, however

[http://deviceguru.com/making-ubuntu-look-like-windows-7/](http://deviceguru.com/making-ubuntu-look-like-windows-7/)

But that wont work with Unity, but try KDE or Kubuntu

I use [http://kde-apps.org/content/show.php/Daisy?content=102077](http://kde-apps.org/content/show.php/Daisy?content=102077)

[http://kde-look.org/content/show.php/Vistar7+-+Windows+7+Transformation+Pack?content=104232](http://kde-look.org/content/show.php/Vistar7+-+Windows+7+Transformation+Pack?content=104232)

---

### Post by linuxuser12345 on 2011-06-19
Is there any other way that doesn't make my system look entirely like Windows 7? I want a system that you can still tell its GNU/Linux, but to have an awesome taskbar like the one on Windows 7. Thanks

---

### Post by pqwoerituytrueiwoq on 2011-06-19
what features in it are you trying to get?
ex:
icon only in task bar
window preview
the one where they all merge under one icon

---

### Post by konsta82 on 2011-06-19
Try installing awn with expand option enabled. I think you can do similar,maybe even better stuff with any other dock applet,but I prefer awn

---

### Post by linuxuser12345 on 2011-06-19
I want something that has a menu button (sort of like the "Start" button"), and icons only in the task bar with window previews and where they all merge into one icon.

---

### Post by Vaphell on 2011-06-19
check various docks like AWN, docky, cairo, dockbarx. They all should be able to group related windows into single icon, pin apps, provide additional functionality like menu with applets.

this clip shows dockbarx
[http://www.youtube.com/watch?v=LiQq9kPsCQE](http://www.youtube.com/watch?v=LiQq9kPsCQE)

---

### Post by linuxuser12345 on 2011-06-19
I tried dockbarx, but it keeps crashing on me... :'(

---

### Post by cbowman57 on 2011-06-19
In addition to what Vaphell suggested, I always liked the look & simplicity of talika.

[http://www.webupd8.org/2010/05/finally-ubuntu-ppa-for-talika-gnome.html](http://www.webupd8.org/2010/05/finally-ubuntu-ppa-for-talika-gnome.html)

---

### Post by linuxuser12345 on 2011-06-19
I want something that is a near-perfect clone of the Windows 7 task bar

---

### Post by asadullah on 2011-06-19
try out gnomenu i was looking for something like what your talking about and it worked for me ```
sudo add-apt-repository ppa:gnomenu-team/ppa
sudo apt-get update
sudo apt-get install gnomenu
```

---

### Post by linuxuser12345 on 2011-06-20
Now how do I erase all of my Gnome panels?

---

### Post by linuxuser12345 on 2011-06-20
> **asadullah said:**
> try out gnomenu i was looking for something like what your talking about and it worked for me ```
sudo add-apt-repository ppa:gnomenu-team/ppa
sudo apt-get update
sudo apt-get install gnomenu
```
I keep getting an error message that says it cannot find the package file or something when in the terminal.

---

### Post by dusanyu on 2011-06-20
try AWN 

sudo apt-get install awn

---

### Post by linuxuser12345 on 2011-06-20
It can't find the packages.
Is there a way I can set it up so this new dock only opens up when I am in Ubuntu Classic mode?

---

### Post by linuxuser12345 on 2011-06-20
I got Talika installed. Now, whenever I go to the "Add to Panel" list, I cannot find the applet... :(

Can someone help me? Thanks! :)

---

### Post by nerdy_kid on 2011-06-20
ok, you want KDE with this:  [https://bitbucket.org/jimi312/smooth-tasks-kde-sc-4.6](https://bitbucket.org/jimi312/smooth-tasks-kde-sc-4.6)  Preview:  [http://kde-look.org/content/preview.php?preview=1&id=99739&file1=99739-1.png&file2=99739-2.jpg&file3=99739-3.png&name=STasks](http://kde-look.org/content/preview.php?preview=1&id=99739&file1=99739-1.png&file2=99739-2.jpg&file3=99739-3.png&name=STasks)


NOTE:  Backup your stuff!! This is going to install ALOT of stuff, and it will totally screw up your Ubuntu desktop -- your Ubuntu will turn into Kubuntu pretty much...so, you have been warned!  ;)   If you do end up doing this I can give you a few tips to speed up KDE and whatnot, I used KDE for a few years before Unity converted me :)

so: 
```

sudo apt-get install kubuntu-desktop
sudo apt-get build-deps plasma-widget-smooth-tasks
sudo apt-get install hg
hg clone https://bitbucket.org/jimi312/smooth-tasks-kde-sc-4.6
cd ./smooth-tasks-kde-sc-4.6
ccmake ./

(change the install prefix to /usr, press "c", and then "g" and "q")

make -j 2
sudo make install[FONT=Verdana]
sudo reboot
[/FONT]
```[FONT=Verdana]
Log in to KDE, and add the "Stasks" plasmoid to the taskbar.  I have no idea how well it works now...I tried it back in 4.6.2 -- KDE's "pinning" ability was kinda (ok, really) buggy.
[/FONT]

---

### Post by linuxuser12345 on 2011-07-01
Is there an easy way I can make a Windows 7-like taskbar in KDE running a widget, so I don't have to run any other programs?

---

### Post by linuxuser12345 on 2011-07-01
PS: Smooth Tasks doesn't work on my system! :(

---

### Post by nerdy_kid on 2011-07-02
whats your system?  The project I linked worked with my 4.7 install -- but I had to compile it -- the prebuilt version crashed plasma.

---

