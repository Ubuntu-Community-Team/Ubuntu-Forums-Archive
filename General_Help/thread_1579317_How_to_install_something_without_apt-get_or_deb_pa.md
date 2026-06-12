---
title: "How to install something without apt-get or deb package manager"
date: 2010-09-21
forum: General Help
---

### Post by mokachoka on 2010-09-21
Hi there,

I have a small touchscreen tablet here thats running a cut down version of ubuntu (i think 9.04). It has its own flash gui and no mention of ubuntu on it anywhere (but i know 100% that it is)....


Anyway, its so cut down it doesnt even have things like apt-get, any file sharing capabilities and it cannot run .deb files.

I can only do things to the filesystem via ssh not using the gui. Its running a busybox shell which is also very limited.

I would ideally like to be able to connect to some nfs shares on my ubuntu server with this thing but im having no luck. I have found out its because it doesnt have nfs-common or portmap installed (apparent dependencies).

My question is, how would i go about manually installing something like that? I need to be pointed in the right direction as atm im not too sure. Baring in mind i cannot simply use apt-get or unpack a .deb file.

Thanks in advance.

---

### Post by bodhi.zazen on 2010-09-21
See this link:

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

Is there a README or specific instructions you can follow ?

---

### Post by mokachoka on 2010-09-21
Hi, thanks for the reply.

I have not been very informative in my first post let me try again...

The tablet touchscreen device has been hacked to install ssh on it and a busybox shell. The manufacture never intended anyone to login to the device this way and start messing about with the files. The OS desktop etc was taken away and a custom flash gui built only letting you run the apps (flash apps) or visit the app store (another flash app) to download new apps (flash).

The underlying system is ubuntu but alot of the things, apt-get, nano, deb package manager etc etc are just not there. Im not sure if this is the shell (busybox) fault though. 

As there is no apt-get, or deb package manager i have no idea how to install an app from scratch. 

The command make doesnt even seem to do anything

# make
-sh: make: not found

edit : could you compile a program on a standard ubuntu install and *transfer* it to this cut down device?

---

### Post by bodhi.zazen on 2010-09-21
You will have a lot of packages to download and compile =). You would probably need to compile some initial packages on an alternate machine and transfer them in an archive.

When you manually install packages you get to identify and resolve all the dependencies.

---

