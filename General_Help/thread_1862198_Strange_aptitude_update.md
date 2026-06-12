---
title: "Strange aptitude update"
date: 2011-10-16
forum: General Help
---

### Post by tommihl on 2011-10-16
I'm getting this after the update 11.04->11.10 :( What are those 404s? Any help will be appreciated.
This is my "aptitude update": [http://paste.ubuntu.com/709958/](http://paste.ubuntu.com/709958/)
And theres my sources.list: [http://paste.ubuntu.com/709966/](http://paste.ubuntu.com/709966/)

There have to be something funny on my sources because im getting prints like these when trying to install something:
```
sudo aptitude install gnome-disk-utility  
[sudo] password for tommih: 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.

```

---

### Post by mcduck on 2011-10-16
You have added some PPA repositories which either don't exist any more, or do not support Ubuntu 11.10.

Remove the extra PPA repositories that are giving you the 404 errors and the problem will disappear.

(PPA's are not include in /etc/apt/sources.list file, they are each configured on separate file inside /etc/apt/sources.list.d directory)

---

### Post by tommihl on 2011-10-16
> **mcduck said:**
> You have added some PPA repositories which either don't exist any more, or do not support Ubuntu 11.10.

Remove the extra PPA repositories that are giving you the 404 errors and the problem will disappear.

(PPA's are not include in /etc/apt/sources.list file, they are each configured on separate file inside /etc/apt/sources.list.d directory)

Removed useless repositories and 404's disappeared. But still cant install some packages likes gnome-disk-utility

---

### Post by mcduck on 2011-10-16
Have you tried with apt-get instead of aptitude?

Could be a problem with the mirror repository as well, I'm using the official repository for Finland and gnome-disk-utility seems to be available without any problems....

---

### Post by tommihl on 2011-10-16
no still the same with the apt-get... is it possible that its already installed but under different "name" or something?..

---

### Post by mcduck on 2011-10-16
> **tommihl said:**
> no still the same with the apt-get... is it possible that its already installed but under different "name" or something?..

What does this command respond:

```
dpkg -s gnome-disk-utility | grep Status
```

The name of the package of course can't change, but sure, it will apppear with a different name in the menus. (simply "Disk Utility" in English, I have no idea about the Finnish translation)


edit: Now that I actually checked, I seem to have it installed. And as I definitely haven't installed it manually I suppose it comes included by default. Makes sense, really, as it was included  by default in previous Ubuntu releases as well.

---

### Post by tommihl on 2011-10-16
> **mcduck said:**
> What does this command respond:

```
dpkg -s gnome-disk-utility | grep Status
```

The name of the package of course can't change, but sure, it will apppear with a different name in the menus. (simply "Disk Utility" in English, I have no idea about the Finnish translation)


edit: Now that I actually checked, I seem to have it installed. And as I definitely haven't installed it manually I suppose it comes included by default. Makes sense, really, as it was included  by default in previous Ubuntu releases as well.

> dpkg -s gnome-disk-utility | grep Status
Status: install ok installed


wtf? tried to remove it and that worked. now installed it back, put cannot find it anywhere and gnome-disk-analyzer dont work :S

---

### Post by mcduck on 2011-10-17
Just press the Super key and type in "disk", it should appear the first in the Dash search.

I've never even heard of "gnome-disk-analyzer". :D If you are looking for the Disk Usage Analyzer, the program's real name is Baobab and I believe it comes with the gnome-utils package. And is installed by default as well...

---

### Post by tommihl on 2011-10-18
> **mcduck said:**
> Just press the Super key and type in "disk", it should appear the first in the Dash search.

I've never even heard of "gnome-disk-analyzer". :D If you are looking for the Disk Usage Analyzer, the program's real name is Baobab and I believe it comes with the gnome-utils package. And is installed by default as well...

I was default in 11.04... Think this topic was solved :)

---

