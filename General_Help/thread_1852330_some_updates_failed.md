---
title: "some updates failed"
date: 2011-09-30
forum: General Help
---

### Post by elliotn on 2011-09-30
this morning I updated my system but then 1mb of files failed, files like nvidia-common etc, I tried a couple of times but it failed

---

### Post by iowabeakster on 2011-09-30
FARK!!!

Me too.

An update on my system (xubuntu 10.04) today has caused an all day headache.  I didn't watch to see if things weren't downloaded, or the wrong things were downloaded, or what.

I ended up manually downloading a linux headers file to get my video driver to install.

My virtual box was fubar'd.

Finally got it working some, but I still can't connect to the virtual machine via ssh (which I need).

And I've just been trying to get all that working again... haven't had any time to try much else...certainly nothing productive.

What a wonderful update that was.

---

### Post by elliotn on 2011-09-30
am still trying but updates still fails, but my system works fine

---

### Post by seawolf167 on 2011-09-30
You are updating with this?

```
sudo apt-get update
sudo apt-get upgrade
```

Maybe that one hosted server is down and it'll work in a couple more hours? Is it the same package(s) for both of you guys?

---

### Post by elliotn on 2011-09-30
> **seawolf167 said:**
> You are updating with this?

```
sudo apt-get update
sudo apt-get upgrade
```

Maybe that one hosted server is down and it'll work in a couple more hours? Is it the same package(s) for both of you guys?

I didn't use the codes but used update manager and synaptic. will try the command line tonight

---

### Post by iowabeakster on 2011-09-30
I doubt it was the same problem for both of us.  I am running Xubuntu 10.04, he was using some version of 11.04.  My problem was with the new kernel in my update.  Originally I also used "update manager".

My problem was initially that I couldn't use my proprietary video driver.  It seemed like the update did not install the appropriate linux headers file.  I used synaptic to get the linux headers file, then I got the driver to compile.

But then my virtual box was fubar'd.  I then got virtual box to run by reconfiguring the kernel modules in vbox.  But I had lost the ability to use a Host only network adapter.  And I couldn't ssh to the virtual system, which I need for a class.

After hours of trying to sort it out, I just gave up and downloaded "startup manger" and reverted to the old kernel.

---

### Post by elliotn on 2011-09-30
ok I should mark this solved. this morning all updates went smooth

---

### Post by seawolf167 on 2011-10-01
Awesome :) glad it all worked out

---

