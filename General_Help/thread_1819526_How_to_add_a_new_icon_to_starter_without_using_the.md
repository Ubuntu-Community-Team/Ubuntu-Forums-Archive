---
title: "How to add a new icon to starter without using the dekstop"
date: 2011-08-06
forum: General Help
---

### Post by regsnerven on 2011-08-06
Hey guys,  i just installed eclipse, the newewst version from the developer website of course, because the one out of the software center is more than outdated. 

Now i have the problem that i don't have any icon in the starter. When i start eclipse i can right click on the icon and make it stick to the startet forever but it has no icon and i can't change it.

 So my question is now: How do i add one to the starter? And i don't want to use the desktop right clicking and create a new starter variation of the solution. 
Firefox has no .desktop file for it's icon in the starter either. 

So, can you tell me how to do this? 

Gr33tZ
 Rn

 P.S.: For the futurue version a right click on the starter->add or right click on and icon->edit would be great.

---

### Post by regsnerven on 2011-08-11
Yeah. A dead forum is a bad thing...

---

### Post by CaptainMark on 2011-08-11
add the ppa for eclipse ```
sudo add-apt-repository ppa:eclipse-team/ppa
``` and then reinstall eclipse from software centre, youll then get the latest version complete with correct icon and will also be kept upto date by the normal update manager

---

### Post by dniMretsaM on 2011-08-11
> **CaptainMark said:**
> add the ppa for eclipse ```
sudo add-apt-repository ppa:eclipse-team/ppa
``` and then reinstall eclipse from software centre, youll then get the latest version complete with correct icon and will also be kept upto date by the normal update manager

I think I'll use this. Have to reinstall all my plugins and stuff though...

---

### Post by CaptainMark on 2011-08-11
maybe, maybe not, it depends, some programs store plugins inside your home folder as hidden config files and they will remain when you uninstall a program and still work when you reinstall, it depends on the plugin and how it was written,

---

### Post by regsnerven on 2011-08-13
W: Fehlschlag beim Holen von [http://ppa.launchpad.net/eclipse-team/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/eclipse-team/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found  W: Fehlschlag beim Holen von [http://ppa.launchpad.net/eclipse-team/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/eclipse-team/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

---

### Post by CaptainMark on 2011-08-14
looking into it more it seems eclipse is still supported in its own ppa, the team has abandoned its launchpad account without closing it down, sorry

---

### Post by regsnerven on 2011-08-16
>  looking into it more it seems eclipse is still supported in its own ppa, the team has abandoned its launchpad account without closing it down, sorry    Which means there is no way to automatically update eclipse from the Software Centre, right?

---

### Post by CaptainMark on 2011-08-16
unless this is the same package, 

[https://launchpad.net/~eclipse-team/+archive/debian-package](https://launchpad.net/~eclipse-team/+archive/debian-package)
 
it has the same name and works on ubuntu, load this ppa and see if it updates eclipse for you, it is still maintained so thats a plus :)
```
sudo add-apt-repository ppa:eclipse-team/debian-package
sudo apt-get update
sudo apt-get install eclipse
```

---

### Post by regsnerven on 2011-08-23
Thanks. Now that we solved that mistery lets get back to topic ^^

---

### Post by CaptainMark on 2011-08-23
ah yeah im not sure why that hasnt sorted the icon im afraid, if you search for eclipse in the dash does it have an icon there??

the .desktop entry should be found in /usr/share/applications and you can open it using the terminal and search  for the icon line to see what the name of the icon is then you should be able to match it to the icon entry in /usr/share/icons if they dont match, then that could be your problem

```
sudo cat /usr/share/applications/*eclipse*.desktop |grep -i icon
find /usr/share/icons -iname "******"
```
the first command should find the .desktop entry and it should just be called eclipse.desktop the second you need to replace the stars for the name from the first command to make sure they match, if not you can change them to match

sorry if ive misunderstood you i think this is what your looking for

---

### Post by regsnerven on 2011-08-28
Not exactly but thanks. That helps me out ;)

---

