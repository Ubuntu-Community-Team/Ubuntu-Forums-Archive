---
title: "Howto install application from mavrik on lucid"
date: 2010-08-22
forum: General Help
---

### Post by ShapeShiftme on 2010-08-22
Good day all. I am using 10.04 64 

i want to use curlftpfs. i installed the program, however it gives errors. by default it installs 09.2.1-build1
and that seems to have a bug on AMD 64. There is apperenlty a fix for this in curlftpfs/0.9.2-2

Which is reallt great news. however i dont know how to install it on 10.04.
As far as i can till there is no 0.9.2.2-2.deb anywhere.
The only place i can find any download is [https://launchpad.net/ubuntu/+source/curlftpfs/0.9.2-2](https://launchpad.net/ubuntu/+source/curlftpfs/0.9.2-2)

If possible could someone please explain to me howto do it.

Regards

---

### Post by ShapeShiftme on 2010-08-22
I found a 9.2-2 deb file. on that page i mentioned above. however it doesnt seem to fix all the problems.

By any change is there another program that does the same thing as curlftps. 

Regards

---

### Post by dino99 on 2010-08-22
here is a french howto translated to english:

[http://translate.google.com/translate?js=y&prev=_t&hl=fr&ie=UTF-8&layout=1&eotf=1&u=http%3A%2F%2Fdoc.ubuntu-fr.org%2Fcurlftpfs&sl=fr&tl=en](http://translate.google.com/translate?js=y&prev=_t&hl=fr&ie=UTF-8&layout=1&eotf=1&u=http%3A%2F%2Fdoc.ubuntu-fr.org%2Fcurlftpfs&sl=fr&tl=en)

even if maverick is in alpha, it is already usable and mostly stable, so you can either make a fresh installation side by side with your lucid (note : 64 bits, in general, have more issues than 32 bits, thats why i use pae kernel (32) for the same advantages minor troubles), or update your sources.list to maverick

---

### Post by ShapeShiftme on 2010-08-22
Thanks for the help.
However im not ready or proficient enough in linux to try an alpha release. i will however make the switch when mavrik becomes beta. is there an eta for that at the moment.

As far as a fix goes i got it working
Curlftpfs gives errors when writing a file and creates a 0 byte file. then if you copy it again it works just fine.
i then tried installing 9.2-2 and that had the same effect so i tried installing an older verion and what do i know it works. curlftpfs_0.9.1-3+b2_amd64 

So if anyone else is having this error give this a try

Regards

---

