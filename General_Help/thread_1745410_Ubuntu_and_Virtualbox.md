---
title: "Ubuntu and Virtualbox"
date: 2011-05-01
forum: General Help
---

### Post by iFuzo on 2011-05-01
Well I am with windows but the only reason is because I produce alot of music in ableton which I couldnt find to work on ubuntu but I had the idea of using a vbox to produce music and browse, social and everything else I would do on the net in ubuntu. Would it be ok to install a virtualbox with 50GB Disk Space and 4GB RAM within ubuntu on my 4GB RAM, 400GB Disk space system?

And as I saw with the new ubuntu I could use workspaces to keep organised but would this work?

---

### Post by scradock on 2011-05-01
> **iFuzo said:**
> Well I am with windows but the only reason is because I produce alot of music in ableton which I couldnt find to work on ubuntu but I had the idea of using a vbox to produce music and browse, social and everything else I would do on the net in ubuntu. Would it be ok to install a virtualbox with 50GB Disk Space and 4GB RAM within ubuntu on my 4GB RAM, 400GB Disk space system?

And as I saw with the new ubuntu I could use workspaces to keep organised but would this work?

You would not be able to assign 4GB of RAM to the virtual machine - Ubuntu needs around 500-800MB just to keep ticking over. Try 3GB for the VM - the disk space is no problem, except that you MUST assign the largest amount of space you will ever need when you set it up, because it's impossible to increase after you've started.

---

### Post by iFuzo on 2011-05-01
Would it be better for me to stick to windows for time being then?

---

### Post by wolfen69 on 2011-05-01
> **scradock said:**
> You would not be able to assign 4GB of RAM to the virtual machine - Ubuntu needs around 500-800MB just to keep ticking over. Try 3GB for the VM - the disk space is no problem, except that **you MUST assign the largest amount of space you will ever need when you set it up,** because it's impossible to increase after you've started.

Not true. During setup of the guest OS, you just select *dynamically expand* (or something similar) hard drive, and the size of the partition will expand automatically as needed. So you can set the initial size fairly small and not worry.

Also, 4gb of ram is way too much for ubuntu in normal use. 2GB will be plenty.

---

