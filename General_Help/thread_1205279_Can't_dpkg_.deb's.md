---
title: "Can't dpkg .deb's?"
date: 2009-07-05
forum: General Help
---

### Post by elcisitiak on 2009-07-05
```
rel@Set:~/Desktop$ sudo dpkg -i dvdshrink_2.6.1-11_all.deb 
Selecting previously deselected package dvdshrink.
(Reading database ... 178294 files and directories currently installed.)
Unpacking dvdshrink (from dvdshrink_2.6.1-11_all.deb) ...
/var/lib/dpkg/tmp.ci/preinst: 5: cannot create /usr/lib/menu/dvdshrink: Directory nonexistent
/var/lib/dpkg/tmp.ci/preinst: 8: cannot create /usr/lib/menu/xbatchrip: Directory nonexistent
dpkg: error processing dvdshrink_2.6.1-11_all.deb (--install):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 dvdshrink_2.6.1-11_all.deb
```I got the same error for k9copy as well. Somebody help me? (God, I'm such a newbie)

---

### Post by wojox on 2009-07-05
Where did you find a DVD Shrink .deb?
It only runs under windows.

---

### Post by p0cky84 on 2009-07-05
1) This really makes me wonder... DVD Shrink in a .deb? == a wolf in sheep's clothing?
2) Have you/ or somebody else been messing with the permissions in /usr/lib/menu/*?

---

### Post by elcisitiak on 2009-07-05
Okay, I guess this is what I get for following tutorials. It was on sourceforge. 

[http://sourceforge.net/projects/dvdshrink/](http://sourceforge.net/projects/dvdshrink/)

I used alien to convert the .noarch.rpm to a .deb . . .

---

### Post by wojox on 2009-07-05
Cool link.
I've been waiting for this for linux. Thanks

Anyway double click the file and it should install if it's .deb

---

### Post by synapsys on 2009-07-05
Try giving it what it wants:

```
cd /usr/lib
sudo mkdir menu
```Then try installing.
Maybe the distro it was meant for has an /usr/lib/menu directory already.
I just checked and I don't have one.

---

### Post by Jebtrix on 2009-07-05
I've had some weird issues with alien sometimes. Another way to do this is just download the vanilla tar.gz package and extract it. In terminal do:

```
sudo apt-get install checkinstall
```
Navigate your way to the dir you extracted to in terminal then:

```
sudo checkinstall -D ./install.sh 
```

This will basically create your own .debian package by monitoring the install. Just a good alternative to be aware of.

Once its done a .deb will be created, but owned by root because it requires sudo to make. So:

```
sudo chown <yourusername> <generated.package.name>.deb 

```

---

