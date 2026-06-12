---
title: "help installing yum"
date: 2006-05-27
forum: General Help
---

### Post by darkstrikera2 on 2006-05-27
ok, so ive googled, and googled, and couldnt find anything on helping me install YUM. i downloaded the 2.6.1 tar.gz and it gives me no help on installing. I would really appreciate the help if any.

thanks in adv.

---

### Post by 2501 on 2006-05-27
I am running 6.06 Dapper Drake RC and if you go to Synaptic you will find it.
I like to use it ...I had a G3 running Yellow Dog and it was a great tool. 

i hope this helps.

-2501

---

### Post by darkstrikera2 on 2006-05-27
it says i must be root :(   with ubuntu, i didnt have a choice of being root.

---

### Post by darkstrikera2 on 2006-05-27
o nvm, i did sudo synaptic in the terminal and it brought it up, im gunna check out what i can install now thanks!

o yeah, and when i go to install something through synaptic, does it like, automatically install on the system (as in none of that tar.gz crap)?

---

### Post by kroiz on 2006-05-27
yes when you install using synaptic it install the program.
with the tar.gz you need to make a few steps before you install:
./configure
make 
sudo makeinstall

But you realy should use synaptic if you find what you want there.
also if you planning on compiling a tar.gz I recommend using checkinstall:
[https://wiki.ubuntu.com/CheckInstall?highlight=%28checkinstall%29](https://wiki.ubuntu.com/CheckInstall?highlight=%28checkinstall%29)

---

### Post by 2501 on 2006-05-27
what .rpm programs are you planning to install that you can not find in Ubuntu????

-2501

---

### Post by johnnyloot on 2006-07-13
hey guys,
im also trying to use yum. 
while after much struggele (didnt know you could install it using synap) I managed to get it installed (so claims synap)

Yet when im in root terminal and type the command yum it is not found.
Do I have to configure anything?

FYI, 
To install it I simply downloaded it and then used
rpm -Uvh yum.2....

help is really appreciated

---

