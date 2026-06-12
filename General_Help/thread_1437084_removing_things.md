---
title: "removing things"
date: 2010-03-23
forum: General Help
---

### Post by mIXpRo on 2010-03-23
hii , 
when using ubuntu specially for new users (like me) we will try to install a lot of things that we doesn't know a lot about to get some issues to be fixed , the problem is that the hardisk gets full so i would like to know what i've installed and how can i remove it .
it's like add/remove software for windows is something like that for ubuntu 9.04 , cause the add/remove software for the ubuntu doesn't list me all the things .

---

### Post by nothingspecial on 2010-03-23
If you`ve only used apt-get/add remove/synaptic ......

.....synaptic does :D

Or are you talking about self compiled binaries, and if you are, which ones.

---

### Post by linden940 on 2010-03-23
applications > ubuntu software center and click on the tab called installed software

it will list what you have installed and you can remove it from there

---

### Post by mIXpRo on 2010-03-23
> **nothingspecial said:**
> If you`ve only used apt-get/add remove/synaptic ......

.....synaptic does :D

Or are you talking about self compiled binaries, and if you are, which ones.

synaptic for example lists what you've installed and what was installed before so you dont know what you've installed .

---

### Post by QIII on 2010-03-23
You are filling up a disk?

How large is it?

Is this a Wubi install?

---

### Post by mIXpRo on 2010-03-23
> **QIII said:**
> You are filling up a disk?

How large is it?

Is this a Wubi install?

it's a metaphor ;) , but all that installations takes a respectable place on the disk .

---

### Post by nothingspecial on 2010-03-23
> **mIXpRo said:**
> synaptic for example lists what you've installed and what was installed before so you dont know what you've installed .

I see what you mean .....

....sorry for the "code"

```
cat /var/log/dpkg.log | grep "\ install\ " | less
```

will list what you`ve installed by date, so you should be able to figure it out from there.

---

### Post by mIXpRo on 2010-03-23
that's exactly what i've been looking for thnx a lot :p

---

### Post by QIII on 2010-03-23
Unless you install everything you can possibly find, it is unlikely that you will ever install enough to fill up your / partition.

Some people think 10G is plenty.  I'd go with 10G + 5G for the OS footprint in most cases.  Remember that you generally don't have to worry about bloat.

If you think you have too much installed, use the Software Center or Synaptic to get rid of them.

Bearing nothingspecial's post in mind, using the Software Center is probably the most safe method here, since  you will not be tempted to uninstall the wrong stuff as you might be in  Synaptic.

So ...

WARNING:  Make sure that what you are uninstalling is something YOU installed.  If you happen to uninstall system files or dependencies for something else, you can entirely bork your system.

---

### Post by philinux on 2010-03-23
> **mIXpRo said:**
> it's a metaphor ;) , but all that installations takes a respectable place on the disk .

Lets have a look how full it is. Post back the results of this.

```
df -h
```

---

### Post by mIXpRo on 2010-03-23
> 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             142G   13G  122G  10% /
tmpfs                 985M     0  985M   0% /lib/init/rw
varrun                985M  108K  985M   1% /var/run
varlock               985M     0  985M   0% /var/lock
udev                  985M  164K  985M   1% /dev
tmpfs                 985M  2.4M  983M   1% /dev/shm
lrm                   985M  2.2M  983M   1% /lib/modules/2.6.28-18-generic/volatile
/dev/sr0              4.0G  4.0G     0 100% /media/cdrom0


why ?

---

