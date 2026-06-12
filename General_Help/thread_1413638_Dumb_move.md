---
title: "Dumb move"
date: 2010-02-22
forum: General Help
---

### Post by diablo69er on 2010-02-22
So I installed adobe reader on my 64 bit nix box, problem is was I used the .deb file with the --force architecture cmd and now I'm unable to remove it.

The command I used was

sudo dpkg -i --force-architecture AdbeRdr9.1.2-1_i386linux_enu.deb

any help would be appreciated.

---

### Post by saturnblackhole on 2010-02-22
you could just go to the synaptic package manager and uninstall it from there. just put adobe in the search box and look for the program you want to delete.

---

### Post by ridetheteapot on 2010-02-22
if you dont see it in synaptic just use the use (i dont think you will. by default it will not list i386 debs)
sudo dpkg -r AdbeRdr
should be good to go.

---

### Post by diablo69er on 2010-02-23
Ok, tried that and here is what I get.

sudo dpkg -r AdbeRdr9.3-1_i386linux_enu.deb

this is displayed

dpkg:  you must specify packages by their own names, not by quoting the names of the files they come in.

So I tried

sudo dpkg -r AdbeRdr 

and this is displayed

dpkg: warning: ignoring request to remove adberdr which isn't installed

help?

---

### Post by scottuss on 2010-02-23
OK, I know that you realise the mistake now, but it has to be said that forcing architecture will cause clowns to eat you. Or something equally horrible...

You could do:
```
locate adobe
``` or
```
whereis adobe
```

Just to check if it is still definitely around, and where.

Edit: Also, what's wrong with Evince? :p

---

### Post by ridetheteapot on 2010-02-23
FYI you can try dpkg --l *{adobe,acro,reader}*
to find package name - which happens to be adobereader-enu

then just use dpkg -r adobereader-enu

---

