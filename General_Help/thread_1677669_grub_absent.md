---
title: "grub absent"
date: 2011-01-29
forum: General Help
---

### Post by c2tarun on 2011-01-29
I read that grub is the default boot loader for ubuntu/kubuntu, but when I am trying to access grub prompt by typing grub on command prompt i get the following message
```

The program 'grub' is currently not installed.  You can install it by typing:
sudo apt-get install grub

```How can this be possible that grub is the default boot loader and not installed on system? OR I am understanding wrong?
please reply
Thanks

---

### Post by coffeecat on 2011-01-29
The package 'grub' is legacy grub, but you are running Lucid/10.04 which uses grub 2. The package for grub2 is 'grub-pc'. have a look in the Synaptic package manager and you'll see that you have grub-pc installed.  Useful link:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

You can run this command to see that you have grub 2:

```
grub-install -v
```

---

### Post by zvacet on 2011-01-29
Why do you need to access grub if you can boot?If you don´t see grub during boot press down shift key and grub will be displayed.Of course you don´t have grub installed because that package is called grub-pc.Grub package is legacy version of grub.

---

