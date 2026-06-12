---
title: "some files can't be deleted"
date: 2012-07-23
forum: General Help
---

### Post by thatjohnpaul on 2012-07-23
So I installed Wine from the Ubuntu Software Center, and suddenly I noticed that some of the fonts changed size in my browser. (I didn't accidentally zoom in or out with ctrl + or -.) I removed Wine in the Software Center and reinstalled Firefox, but the font problem remained. So I went around trying to clean up any remaining Wine files, and found some, but when I right-click and try to delete them, it doesn't give me the option. Here's a screenshot for reference.

[http://img811.imageshack.us/img811/8645/screenshotat20120723214.png](http://img811.imageshack.us/img811/8645/screenshotat20120723214.png)

---

### Post by raja.genupula on 2012-07-24
you have to do purging to remove all files about wine .

```
sudo apt-get purge wine 
```

for more information you can read this [https://help.ubuntu.com/community/AptGet/Howto#Removal_commands](https://help.ubuntu.com/community/AptGet/Howto#Removal_commands)

---

### Post by thatjohnpaul on 2012-07-24
> **raja.genupula said:**
> you have to do purging to remove all files about wine .

```
sudo apt-get purge wine 
```for more information you can read this [https://help.ubuntu.com/community/AptGet/Howto#Removal_commands](https://help.ubuntu.com/community/AptGet/Howto#Removal_commands)

Okay, I tried that, and this is what I got:

```
jp@jp-Inspiron-1545:~$ sudo apt-get purge wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is not installed, so not removed
The following packages were automatically installed and are no longer required:
  gettext libunistring0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 431 not upgraded.
jp@jp-Inspiron-1545:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```

---

### Post by raja.genupula on 2012-07-24
while doing autoremove you must be root . 

while coming to your wine issue ..its saying that its not found any . But as you mentioned in your image you got somefiles with name as wine . if you want to delete them you must be root .

---

### Post by thatjohnpaul on 2012-07-24
> **raja.genupula said:**
> while doing autoremove you must be root . 

while coming to your wine issue ..its saying that its not found any . But as you mentioned in your image you got somefiles with name as wine . if you want to delete them you must be root .

Thank you! That worked for most of them, but there are a couple files left. This is the what I get when I try to remove them as the root. Any idea how I can delete them?

```
jp@jp-Inspiron-1545:~$ sudo rm /usr/share/doc/ttf-liberation
[sudo] password for jp: 
rm: cannot remove `/usr/share/doc/ttf-liberation': Is a directory
jp@jp-Inspiron-1545:~$ sudo rm /usr/share/doc/ttf-mscorefonts-installer
rm: cannot remove `/usr/share/doc/ttf-mscorefonts-installer': Is a directory

```

---

