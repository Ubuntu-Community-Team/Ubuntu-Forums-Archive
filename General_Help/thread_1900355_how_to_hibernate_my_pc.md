---
title: "how to hibernate my pc"
date: 2011-12-26
forum: General Help
---

### Post by shubham1 on 2011-12-26
how to hibrnate my pc
there is no hibernate option then i installed hibernate using apt-get
then i did a sudo hibernate
it says
```

Some modules failed to unload: nvidia
hibernate: Aborting suspend due to errors in ModulesUnloadBlacklist (use --force to override).

```
but when i used --force it did an it worked it was saying cant do nvdia like something
then at second time when i used the same method it does not works

---

### Post by techvish81 on 2011-12-26
> **shubham1 said:**
> how to hibrnate my pc
there is no hibernate option then i installed hibernate using apt-get
then i did a sudo hibernate
it says
```

Some modules failed to unload: nvidia
hibernate: Aborting suspend due to errors in ModulesUnloadBlacklist (use --force to override).

```
but when i used --force it did an it worked it was saying cant do nvdia like something
then at second time when i used the same method it does not works

Which version and flavour of ubuntu you are using. Gnome, xfce, kde etc..?

---

### Post by shubham1 on 2011-12-26
> **techvish81 said:**
> Which version and flavour of ubuntu you are using. Gnome, xfce, kde etc..?
ubuntu  normal variant
11.10 or 12.04 most probably its 11.10 as it has no features of 12.04 but i have upgraded to 12.04 but it shows 11.10 every where and is 11.10 but system monitor shows 12.04 but it is 11.10

---

### Post by shubham1 on 2011-12-28
any one who could help me i have given full info

---

### Post by plucky on 2011-12-28
> **shubham1 said:**
> ubuntu  normal variant
11.10 or 12.04 most probably its 11.10 as it has no features of 12.04 but i have upgraded to 12.04 but it shows 11.10 every where and is 11.10 but system monitor shows 12.04 but it is 11.10

Post output of ```
lsb_release -a
```

I have a dual boot 11.10 and 12.04.

I can hibernate in 11.10,but there is no option to hibernate in 12.04 so it might be broken if you are running 12.04.

---

### Post by 3rdalbum on 2011-12-28
1. If you've upgraded to 12.04, then you should try posting in the Precise Pangolin forum on Ubuntu Forums.

2. Thanks for helping test Precise, but if you've only been using Ubuntu since this year you might want to stick to release versions. 12.04 is at a very early stage of development and there will be breakage. If your system is pretty good as it is now, then I'd recommend not running any updates until the last Alpha or first Beta.

It's good that you're enthusiastic for testing though :-)  I wish more  Ubuntu users would test development versions and report bugs!

---

### Post by shubham1 on 2011-12-28
> **plucky said:**
> Post output of ```
lsb_release -a
```I have a dual boot 11.10 and 12.04.

I can hibernate in 11.10,but there is no option to hibernate in 12.04 so it might be broken if you are running 12.04.
i have no dual boot
i can hibernate using
sudo hibernate --force
but if i remove my usb devices hibernate fails does it nees my usb drive that connects to internet to upload image at ubuntu one

---

### Post by shubham1 on 2011-12-28
> **3rdalbum said:**
> 1. If you've upgraded to 12.04, then you should try posting in the Precise Pangolin forum on Ubuntu Forums.

2. Thanks for helping test Precise, but if you've only been using Ubuntu since this year you might want to stick to release versions. 12.04 is at a very early stage of development and there will be breakage. If your system is pretty good as it is now, then I'd recommend not running any updates until the last Alpha or first Beta.

It's good that you're enthusiastic for testing though :-)  I wish more  Ubuntu users would test development versions and report bugs!
thanks ok i will post in precise penglin forum i think it is a bug
i have tried a lot when ubuntu 11.10 beta was lauched to test but i cant
may times i upgraded for hours downloaded images but nothing happened download breaks then i installed 11.10 final when and removed my 11.04 and start from a completely new thing
[http://ubuntuforums.org/showthread.php?t=1856403](http://ubuntuforums.org/showthread.php?t=1856403)
[http://ubuntuforums.org/showthread.php?t=1853345](http://ubuntuforums.org/showthread.php?t=1853345)
[http://ubuntuforums.org/showthread.php?t=1852449](http://ubuntuforums.org/showthread.php?t=1852449)
[http://ubuntuforums.org/showthread.php?t=1841384](http://ubuntuforums.org/showthread.php?t=1841384)
and many more

---

### Post by shubham1 on 2011-12-28
> **plucky said:**
> Post output of ```
lsb_release -a
```I have a dual boot 11.10 and 12.04.

I can hibernate in 11.10,but there is no option to hibernate in 12.04 so it might be broken if you are running 12.04.
```
Distributor ID:    Ubuntu
Description:    Ubuntu precise (development branch)
Release:    12.04
Codename:    precise

```

---

