---
title: "How to use terminal to go upto my usb external harddrive?"
date: 2009-07-08
forum: General Help
---

### Post by draperdt on 2009-07-08
I have my 200gb external hard drive mounted in /media/New Volume. I am fine with it. It has NTFS partition but it auto mounts and stores my music which I stream to an xbox using samba.

I have noticed that my media folder under root is now cluttered with useless folders since I was trying options to auto mount and figuring out how to give access to xbox so it can see the folder.

Now my next aim is to dig into fstab and know more about hard drives and how they function in unix like systems.

But before I jump into that, I was wondering if some one can tell me how to reach my external folder from within a terminal. 

Typical ls function shows me Desktop downloads Pictures and all that. How do I get to /media/New Folder ? 

Sorry if its a dumb question. I just need this help and I think it will help me remove some of the negative block I have against terminal and hard drives.

---

### Post by kpkeerthi on 2009-07-08
cd /media/New[press TAB key]

---

### Post by draperdt on 2009-07-08
No. I am sorry, the external hardrive wasnt infact mounting at boot. I assumed wrong. I will go back to working on mounting it at boot.

---

### Post by del_diablo on 2009-07-08
Adding a line to /etc/rc.conf or whatever it was again could work.
mount -a
:P

---

