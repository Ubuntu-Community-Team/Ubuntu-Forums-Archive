---
title: "how to change the apt-get installation directory"
date: 2011-01-07
forum: General Help
---

### Post by sysabod on 2011-01-07
[SIZE=2]Hi all;
        i used to use synaptic to install packages which seems to be installed somewhere like /usr/bin or /usr/local/bin, so my question is can i change the default or pre-determined installation directory, coz my partition / is kind of short of space.[/SIZE]

Thanks in advance !

---

### Post by dcstar on 2011-01-07
> **sysabod said:**
> [SIZE=2]Hi all;
        i used to use synaptic to install packages which seems to be installed somewhere like /usr/bin or /usr/local/bin, so my question is can i change the default or pre-determined installation directory, coz my partition / is kind of short of space.[/SIZE]

Thanks in advance !

You cannot, they are standard locations set by the package creators.

---

### Post by Yougo on 2011-01-07
don't take my word for it, but would it be possible to create a partition, copy the contents of /usr/local/bin to that partition, and mount that partition at /usr/local/bin in your fstab?

it works for /home, but then again, that is not root-owned :-/

---

### Post by MaxIBoy on 2011-01-07
Yeah, it's just not going to happen, because in each package, different bits and pieces go all over the place. Try freeing up some space or expanding the partition.

---

### Post by piquat on 2011-01-07
> **Yougo said:**
> don't take my word for it, but would it be possible to create a partition, copy the contents of /usr/local/bin to that partition, and mount that partition at /usr/local/bin in your fstab?

it works for /home, but then again, that is not root-owned :-/

Isn't bulk of an app usually in /opt?

As I understood it, and I may very well be wrong, if you had made those extra partitions during install and mounted them in their respective places in the file system, you could have avoided this.

Correct?

---

### Post by MaxIBoy on 2011-01-07
Uh, no. I have 325 mib in /opt, out of 10 gigs in /.

Solutions involving moving specific directories are not going to work. I only have 297 mib in /usr/bin for example. No one directory is going to have more than a gig or so, but it adds up.

---

### Post by Yougo on 2011-01-07
> Isn't bulk of an app usually in /opt?

As I understood it, and I may very well be wrong, if you had made those extra partitions during install and mounted them in their respective places in the file system, you could have avoided this.

Correct?

well, i suppose so, but thats in hindsight. besides, if the OP has to resort to a fresh install (which he doesnt just yet, imo), he might as well create a bigger primary partition to begin with :)


expanding your partition might work, but that's tricky business. i've srewed up systems with that before.

---

### Post by piquat on 2011-01-07
> **MaxIBoy said:**
> Uh, no. I have 325 mib in /opt, out of 10 gigs in /.

Solutions involving moving specific directories are not going to work. I only have 297 mib in /usr/bin for example. No one directory is going to have more than a gig or so, but it adds up.

After looking, you are correct, don't know where I got that idea.

78% of my usage is in /usr.  It's mainly split between /lib and /share.  /lib is 36% and /share is 55% of that 78% in /usr.

4.3G total and 3.3G of that is in /usr.  I could have put it on it's own partition.  Or for my SSD at home, put that all on the mech. drive.

Sorry for the hijack, it's a subject I've been interested in.

---

### Post by MaxIBoy on 2011-01-07
You're still better off with one big partition for /, it's the most efficient use of free space. (I learned this the hard way.)

Try freeing up some space (you'd be surprised how easy this is; delete old kernels, clear out your apt cache, uninstall auto-removable packages, etc.) And if you have to resort to messing with your partition table, the best thing is to resize your existing partitions, not add new ones.

(By the way, carrying on with the thread jack, / is actually a better choice for an SSD than /home, because / is where you actually want things to be fast.)

---

