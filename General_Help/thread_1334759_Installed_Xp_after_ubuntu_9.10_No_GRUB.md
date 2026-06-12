---
title: "Installed Xp after ubuntu 9.10: No GRUB"
date: 2009-11-22
forum: General Help
---

### Post by dbzkid on 2009-11-22
How can I fix this? I reformated my xp partition and already had ubuntu 9.10 installed now it just uses the windows loader. Also it does have grub 1.97 beta on my machine (I dont know if that matters) because I tried using the older methods and got nothing.

Thanks,
Kevin

---

### Post by running_rabbit07 on 2009-11-22
Read the thread in [this link]("http://ubuntuforums.org/showthread.php?t=224351") and it will get you up and running in no time.:)

---

### Post by dbzkid on 2009-11-22
It isnt working, I run my install disk and i get this

```
ubuntu@ubuntu:~$ sudo grub
sudo: grub: command not found
ubuntu@ubuntu:~$ 

```

These tutorial is for the older version of grub/ubuntu. it isnt seeming to work with 9.10

---

### Post by running_rabbit07 on 2009-11-23
I don't think I have seen anything for the new grub yet.

---

### Post by r_s on 2009-11-23
It's just that windows overwrites it and you need to install your grub all over again , but ubuntu 9.10 comes with grub2 so the usual commands won't work and also there is no menu.lst in grub2 . Search the forums for more help.
[http://linuxers.org/howto/how-recover-grub2-ubuntu-910-karmic-koala](http://linuxers.org/howto/how-recover-grub2-ubuntu-910-karmic-koala)

---

### Post by running_rabbit07 on 2009-11-23
> **r_s said:**
> It's just that windows overwrites it and you need to install your grub all over again , but ubuntu 9.10 comes with grub2 so the usual commands won't work and also there is no menu.lst in grub2 . Search the forums for more help.
[http://linuxers.org/howto/how-recover-grub2-ubuntu-910-karmic-koala](http://linuxers.org/howto/how-recover-grub2-ubuntu-910-karmic-koala)

That looks like it should work. I did the upgrade to Karmic, so I am still using Grub 1.5.

---

### Post by dbzkid on 2009-11-23
this was a clean install of 9.10... thank you so far.

-Kevin

---

