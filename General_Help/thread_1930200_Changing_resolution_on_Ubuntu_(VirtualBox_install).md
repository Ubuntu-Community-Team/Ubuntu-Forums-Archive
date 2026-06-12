---
title: "Changing resolution on Ubuntu (VirtualBox install)"
date: 2012-02-23
forum: General Help
---

### Post by Angus Munro on 2012-02-23
Hi there, 

This has probably already been posted and closed but i cant for the life of me find a thread on it.

I have installed Ubuntu 11.10 on the latest version of VB. i am running windows 7 x64 Ultimate.

I cant seem to get Ubuntu to fullscreen to my native resolution of 1920x1080...the option is just not there under settings and display. I have installed the guest additions but still no joy.

Any clues?

---

### Post by winh8r on 2012-02-23
Not 100% sure on this but I think you need to open a terminal in the Ubuntu 11.10 installation and enter:


```
sudo apt-get install virtualbox-guest-dkms
```

then you should be able to alter things like resolution and folder sharing etc.

(I am running 10.04 at the moment and 11.10 is in Vb on another machine)

---

### Post by Angus Munro on 2012-02-23
Thanks for getting back to me, i installed those packages and everything is working great. If i could give you karma i would.

Big thanks! :D

---

### Post by winh8r on 2012-02-24
No problem, Just glad that my memory is still working fairly well though!!!


Could you please use the thread tools tab at the top of the page and mark this as solved, thanks.

Good Luck

---

