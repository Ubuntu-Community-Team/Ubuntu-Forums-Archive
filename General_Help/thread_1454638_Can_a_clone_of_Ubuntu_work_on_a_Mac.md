---
title: "Can a clone of Ubuntu work on a Mac?"
date: 2010-04-14
forum: General Help
---

### Post by Ubu4moi on 2010-04-14
I would like to clone an existing desk top installation of Ubuntu Ultimate Edition and run it on my MacBook, can it work? What do I have to do to get it running there?

---

### Post by duanedesign on 2010-04-15
You could use something like 'dd' or 'clonezilla' but then you would also need to install grub2 to be able to boot it. Most the guides out there for cloning your Ubuntu install are for installs using Grub legacy. Grub2 might be a little trickier. 

If you just want to make a copy of installed applications you could use.

To save the list of installed packages.
```
dpkg --get-selections | awk &#8216;$2 ~ /^install$/ {print $1}&#8217; > installedpackages
```

To install from the list.
```
cat installedpackages | xargs sudo aptitude install -y
```

If you have enabled any extra repositories you would need to enable those on the machine you are transferring to.

After installing the packages you could then copy over your $HOME directory and you would have a set-up that was very close to your old one. Someone might argue otherwise but I think this would be easier than trying to clone your install. Especially if you are dealing with drastically different hardware.
-
-

---

