---
title: "is there anyway to install kubuntu thou ubnutu to triple boot?"
date: 2009-09-17
forum: General Help
---

### Post by thenoobguru on 2009-09-17
i want to try kubuntu but i want to keep ubuntu, and i dont want to boot back to vista to install kubuntu. is this possible?

---

### Post by undecim on 2009-09-17
You can, if you really want to, provided you share swap partitions between the two, because you have 4 primary partitions on a hard drive. If you have one for each OS and a swap partition for your Linux OSs, this works fine (provided that if you hibernate from one Linux OS, you resume to that same one, because the swap stores info in hibernate)

Or, better yet, you can just run this command:

```
sudo apt-get install kubuntu-desktop
```

that will install all the packages for Kubuntu onto your current Ubuntu installation. Then when you log in, you should be able to choose between gnome (Ubuntu interface) or KDE (Kubuntu interface)

---

### Post by slakkie on 2009-09-17
Yes, but you don't need a triple boot for that..
Just install the kubuntu-desktop package, logout of your current GUI session, select the correct session type (KDE) and login.

```

dpkg --get-selections > installed.pkgs
sudo aptitude install kubuntu-desktop
dpkg --get-selections > installed_kubuntu.pkgs

```

Why do I run get-selections twice? In case you don't like the Kubuntu desktop you can easily remove it by doing:

```

for i in $(diff -ur installed.pkgs installed_kubuntu.pkgs | tail -n +3 | grep "^+" | sed -e 's/+//g' ) ; do
echo "$i\tpurge"
done > remove.kubuntu
sudo dpkg --set-selections < remove.kubuntu
sudo apt-get dselect-upgrade

```

---

### Post by WinterMadness on 2009-09-17
as the user above said, do:
```

sudo apt-get install kubuntu-desktop
```

if you install another partition just for kubuntu its a waste, they are not different operating systems. they are the same os with a different desktop environment, which you can switch between when you login.

---

### Post by wilee-nilee on 2009-09-17
This site is a great resource for what yoiu need to know, I also would install with 
sudo aptitude in that it remebers all installed for easy removal.
 
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

