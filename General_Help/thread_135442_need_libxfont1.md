---
title: "need libxfont1"
date: 2006-02-23
forum: General Help
---

### Post by rollininoh on 2006-02-23
trying to instal xgl and compiz on a toshiba m35x-s161, but i cant seem to apt-get libxfont1, it tells me its unavailable or obsolete . 

I am a total linux newb, can anyone help me with instructions? i will give up microsoft forever if i can get the cube to work lol!

---

### Post by nanotube on 2006-02-23
well, if you open up synaptic, and search for libxfont, it will show up...
if not, hit reload, and try again.
its in the default repositories, so should be there.

---

### Post by Xian on 2006-02-23
Use this link and download/install locally: [libxfont1_0.99.0-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libx/libxfont/libxfont1_0.99.0+cvs.20050909-1_i386.deb). Download to your /home/username directory, open a terminal (Applications > Accessories >Terminal) and issue this command:

$ sudo dpkg -i *.deb

---

### Post by rollininoh on 2006-02-23
thanks so much! i tried synap but it diesnt show up for me, do i need to update sources or something? 

link works for me though, thanks for the help!

---

### Post by nanotube on 2006-02-24
well... i dont know what's up with your synaptic, maybe its the sources.
click the link in my sig, and go to the sources.list section. try using my sources.list, and see if that helps any...

---

