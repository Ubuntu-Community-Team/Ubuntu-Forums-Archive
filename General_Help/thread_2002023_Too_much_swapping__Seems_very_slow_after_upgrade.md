---
title: "Too much swapping?  Seems very slow after upgrade"
date: 2012-06-12
forum: General Help
---

### Post by petermg on 2012-06-12
After I upgraded to 12.04 it seems my system does a TON of swapping.  I am wondering if there was a problem during the upgrade?  The version prior didn't have this issue.  I don't know how to troubleshoot it but when it gets slow the hard drive light goes crazy so I know it's swapping, at least I don't know what else it could be.  Thanks for any help.

---

### Post by Yellow Pasque on 2012-06-12
You should check on memory usage when it starts swapping:
```
free -m
```

If it is going swap crazy, then something's hogging the RAM, so find out what it is:
```
sudo apt-get install htop
sudo htop
```

---

### Post by irv on 2012-06-12
Another thing you can do to see what is going on with your CPU usage is to run this command:
```
top
```
There is also a utility call htop. If you install it by using
```
sudo apt-get install htop
```
then at the command line just run.
```
htop
```
This will at least show you what is running and how much CPU usage is going on.

---

### Post by neu5eeCh on 2012-06-12
I've been having the same problem. At first I thought it was Google Chrome, but now I think it's FF's plugin-container. If you're using FF, start up your system monitor and check to see the size of FF's plugin-container. Then again, your problem may have nothing to do with this.

---

### Post by petermg on 2012-06-13
[QUOTE=Temüjin;12020266]You should check on memory usage when it starts swapping:
```
free -m
```



```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          1001        908         92          0         51        227
-/+ buffers/cache:        629        371
Swap:         1607          0       1607
```
Looks like most of the RAM is already used!?

---

### Post by petermg on 2012-06-13
> **VTPoet said:**
> I've been having the same problem. At first I thought it was Google Chrome, but now I think it's FF's plugin-container. If you're using FF, start up your system monitor and check to see the size of FF's plugin-container. Then again, your problem may have nothing to do with this.

I don't really use FF, I have it installed but I use Chrome.

---

### Post by joe4ska on 2012-06-13
I'd suggest trying Midori Lightweight Web Browser  It's not perfect but it will save some ram.

> sudo apt-get install midori

[http://twotoasts.de/index.php/midori/](http://twotoasts.de/index.php/midori/)

I'm running it now and it appears to be only using 60MB to start.

WIth 1GB you may need to get creative and try out some lightweight applications 

The ArchLinux wiki has a good list and you can find most of this stuff in the software center [https://wiki.archlinux.org/index.php/Common_Applications]("https://wiki.archlinux.org/index.php/Common_Applications")

---

### Post by roelforg on 2012-06-13
You might want to look into other de's as well.
I, for one, always install lxde (no lubuntu-desktop, just apt-get install lxde) so that i have a super light de ready when i need a lot of ram.
I've had systems run smooth on lxde that had 256 mb ram, they only went swapping when ff loaded a page with a lot of images (and i didn't even dare to use google images because the swapping would get totally out of control with that site, i needed to pull the ethernet cable and wait for ff to time out before my computer became usable again.

---

### Post by Yellow Pasque on 2012-06-13
> **petermg said:**
> Looks like most of the RAM is already used!?

About 600MB of 1GB (and no swap is being used), so that's okay. Something else must be pegging the HD.

---

### Post by vasa1 on 2012-06-13
> **petermg said:**
> I don't really use FF, I have it installed but I use Chrome.
Which features of Chrome have you enabled in Advanced Settings?

---

