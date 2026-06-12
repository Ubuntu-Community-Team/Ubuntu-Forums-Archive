---
title: "GPARTED doesn't start"
date: 2010-05-03
forum: General Help
---

### Post by leoh on 2010-05-03
Hi everyone.
I am running Ubuntu 10.04 x64.
I upgraded recently from 9.10. Back then I had manually upgraded GPARTED to the latest version because I needed a new feature not available on the repository version. And it was working just fine.
However, after upgrading, I click on GPARTED, I get a "GPARTED loading" window, and then nothing happens.
So I decided to start it by command line and this is what I get:

```
$ sudo gparted
/usr/local/sbin/gpartedbin: error while loading shared libraries: libparted-1.8.so.12: cannot open shared object file: No such file or directory
```

Under /usr/local/sbin I have 2 files: gparted and gpartedbin, and they are not empty.

I already tried to reinstall from synaptics, but still the same result.
What can I do?

---

### Post by oldos2er on 2010-05-03
What happens if you run /usr/sbin/gparted ?

---

### Post by leoh on 2010-05-04
> **oldos2er said:**
> What happens if you run /usr/sbin/gparted ?

Running either file (gparted or gpartedbin) gives the same output as before:

```
error while loading shared libraries: libparted-1.8.so.12: cannot open shared object file: No such file or directory
```

I searched on Synaptic for libparted-1.8.so.12 and I couldn't find it. There are similarly named packages, some are installed and some are not.

What can I do?

The situation is that I have a dual boot system (Ubuntu + Win), and need to resize the partitions so that I move free space from one to the other. Would it be a good idea to use Ubuntu 10.04 live CD and resize with GPARTED?
If not, what other live distro can you recommend to achieve it?

Anyway, I would like to fix the gparted issue.

---

### Post by dino99 on 2010-05-04
into synaptic: remove/purge gparted, then reinstall it

sudo dpkg --configure -a

better than gparted, search partedmagic on web

---

### Post by oldos2er on 2010-05-04
I'm using Lucid, and it seems some of the library files used by gparted have changed/been renamed. Using the 10.04 LiveCD to make changes to your partitions sounds like a good idea.

Just a thought, but have you run **sudo apt-get update && sudo apt-get upgrade** lately?

---

### Post by leoh on 2010-05-04
> **dino99 said:**
> into synaptic: remove/purge gparted, then reinstall it

sudo dpkg --configure -a

better than gparted, search partedmagic on web

I am using Ubuntu in Spanish and I couldn't find any "purge" option, I am assuming it is the equivalent to the "Uninstall completely" in the menu.
I did that, then ran the line you gave me, then installed again. No change, still the same situation.

---

### Post by leoh on 2010-05-04
> **oldos2er said:**
> have you run **sudo apt-get update && sudo apt-get upgrade** lately?

Did that, nothing changed. It didn't install anything since the system is already up to date and running 10.04.

---

### Post by oldos2er on 2010-05-04
Your user info says you're running Karmic.

You do have libparted0debian1 installed, I guess?

---

### Post by leoh on 2010-05-06
> **oldos2er said:**
> Your user info says you're running Karmic.

You do have libparted0debian1 installed, I guess?

Actually, it's not my system, it's my mother's. As I said on the first post, it's running Ubuntu 10.04 x64, upgraded recently from 9.10 x64. Everything is running fine except this.
And yes, I have libparted0debian1 (2.2-5ubuntu5) installed.
What can I do to make it work?

---

### Post by buntu63 on 2011-09-22
Idem!

---

### Post by oldos2er on 2011-09-22
Closed for necromancy.

---

