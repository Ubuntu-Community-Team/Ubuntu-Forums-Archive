---
title: "How to download ubuntu software's or apps on windows?"
date: 2011-02-26
forum: General Help
---

### Post by kithusan on 2011-02-26
hi 
   i have ubuntu 10.10 desktop... :D
   so i want to download software's like (Wine HQ or games and other apps)
   but the problem is that i have very very slow ( dial up connection):(:(
   so what i do is go to a library and they have free wifi.. so i use my WINDOWS LAP to 
   to download things and used to transfer download to my windows vista desktop but now i
   have ubuntu 10.10 desktop.:confused::confused:


   so i'm wondering is there any software for free which i could download apps for ubuntu
   on my windows 7 and transfer to ubuntu.:D

---

### Post by whatthefunk on 2011-02-26
You can download from the repository and save the files on a USB stick.
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Most of the files from the repository contain a text file called INSTALL that tells you how to install the program.  Most of them need to be installed through the command line.  The easiest way, however, is to download .deb files because then all you have to do is double click on them and they install themselves.  

The problem you will likely have is that a lot of programs have other programs and files that they depend on and so when you try to install them you may get error messages telling you that you need to first install some other program.  These other programs also have dependencies and so you may be making a lot of trips to the library.

---

### Post by gerowen on 2011-02-26
If you could download the .deb files from the site they should install just fine as long as there are no weird dependencies.

---

### Post by seawolf167 on 2011-02-26
> **gerowen said:**
> If you could download the .deb files from the site they should install just fine as long as there are no weird dependencies.

+1 for this - if you can find .deb files it would be much simpler

If you cannot and have to build a lot from source, I suggest looking at using checkinstall to build the packages

then when building substitute checkinstall for install, i.e.

```
./configure
make
sudo checkinstall
```

---

### Post by kithusan on 2011-02-27
thanks guys   

but do you know any place ( website's) where i can find[COLOR=Red] .deb[/COLOR]

---

### Post by kithusan on 2011-02-28
thanks guys that helped

---

