---
title: "moving installed packages"
date: 2009-07-23
forum: General Help
---

### Post by bubblez-gopop on 2009-07-23
Hi, switched from windows to linux, ubuntu to be more precise :D, a few months back and up until now i've been able to work out problems either by google searching or just mucking around but i'm buying a new laptop and i'd like to know if there is anyway to either move my whole ubuntu installation or just the installed packages to my new laptop. I would just download them all again but I dont get much broadband usage and dont realy want to waste it all if i dont have to. any help would be appreciated even just an explanation as to why i cant do this, if thats the case.
Thanks :)

---

### Post by NightwishFan on 2009-07-23
Yes you can.

Install aptoncd. Then have it make an install DVD of all your packages. The new Ubuntu install will autodetect the CD, and add the packages to synaptic package manager. Make sure you use the same version and architecture of Ubuntu as the current one.

```
sudo apt-get install aptoncd
```


Aptoncd is actually a graphical application, so you should understand it fine. Please ask if you need any help.

EDIT: Link to help on aptoncd

[https://help.ubuntu.com/community/APTonCD](https://help.ubuntu.com/community/APTonCD)

---

### Post by cariboo on 2009-07-23
You can use [Remastersys]("http://www.geekconnection.org/remastersys/remastersystool.html") to create a live cd of your installation, which you can then run on your laptop.

---

### Post by tuxxy on 2009-07-23
You could create a separate /home partition for your current Ubuntu installation which you can then mount as the /home for your new laptop Ubuntu installation.  

This will save all your application config and personal files from your old installation, which means you just have to install the actual applications again from the repository, once installed they will already be configured just as you like them.

[http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)

---

### Post by bubblez-gopop on 2009-07-23
Thanks heaps, didn't expect such a fast reply lol :)

---

### Post by NightwishFan on 2009-07-23
You are part of "the machine" now. Welcome.

---

### Post by bubblez-gopop on 2009-07-23
Thanks, i'm glad to finaly be a part of the ubuntu community eve if it is just getting some help at the moment but hopefully i'll be able to do the same for others.

---

### Post by Rodemire on 2009-07-24
Thanks a lot for this help. I had the same problem. I used APTonCD and it made an image of all my apt packages. The interface is quite easy to use.

Thanks again.

---

