---
title: "Internet using Ubuntu live cd"
date: 2010-12-18
forum: General Help
---

### Post by Adityapolo on 2010-12-18
Is it possible to use internet, download and install applications while using Live cd. If yes then please explain me how to do it. I use broadband connection and finding it difficult to establish connection.

---

### Post by Torombolo on 2010-12-18
you can, but it wont mater, if you have to restart the "Live Cd" nothing will be saved, unless you use a persistence installation in a USB.

---

### Post by whtlime on 2010-12-18
> **Adityapolo said:**
> Is it possible to use internet, download and install applications while using Live cd. If yes then please explain me how to do it. I use broadband connection and finding it difficult to establish connection.

It is possible, but anything you do while running the live CD will not be saved. To do so, you insert the live disks and follow the prompts to run it live.

It will bring you in to the Ubuntu OS and you will know you are in once you see an 'Install Ubuntu' icon on the desktop.

To install applications, select applications from the top panel and select Ubuntu software center. Once you're in, you can search for the software you want. If you don't have a specification, you can browse by category.

Once you find the application you want, select install. Done!

I should mention, in order to install these you need an internet connection. Broadband or wireless, does not matter. They decide the speed at which your application is downloaded.

 - whtlime

---

### Post by Adityapolo on 2010-12-18
Its no problem if it gets lost once I restart (I just want to try it). I am having problem in configuring the internet connection. _I can't connect to internet_, that's the actual problem. Please tell me how to set up my connection.

---

### Post by Torombolo on 2010-12-18
you cannot connect what state? Wireless or Ethernet?

---

### Post by Adityapolo on 2010-12-18
Its _ethernet_. I had used Ubuntu inside a virtual box and it worked fine and automatically detected the internet, but that's not the case with live cd. I know how to create a new internet connection in Windows but nothing about it in Ubuntu. Please help.

---

### Post by Torombolo on 2010-12-18
it should had worked plug and play....

Umm one sec... well in backtrack i use

```
sudo /etc/init.d/networking start
```

in the terminal


seems to work in ubuntu also, try it

---

