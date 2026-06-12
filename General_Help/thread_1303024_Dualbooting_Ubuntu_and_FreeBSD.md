---
title: "Dualbooting Ubuntu and FreeBSD"
date: 2009-10-27
forum: General Help
---

### Post by absolutezero1287 on 2009-10-27
So I've decided to learn about FreeBSD by dualbooting it with Ubuntu 9.04.

However, there are a few things that I need to take care of.

-I need Ubuntu to recognize my FreeBSD partition
-I need to be able to share swap space between the two

What I've done so far:
I've added support for UFS but gparted marks the partition as "unknown".

Read about sharing swap between the two operating systems at [http://tldp.org/HOWTO/Linux+FreeBSD-3.html](http://tldp.org/HOWTO/Linux+FreeBSD-3.html) however the instructions don't really seem to be geared towards Debian-based distros.

Can anyone help?

---

### Post by absolutezero1287 on 2009-10-31
Seriously? No one knows how to share swap between FreeBSD and Ubuntu? Can anyone at least point me to the script that mounts the swap space on Ubuntu?

Any help would be appreciated.

---

### Post by absolutezero1287 on 2009-10-31
Ok so someone on Freenode's #Debian was kind enough to let me know that /etc/init.d/checkroot.sh and mountall.sh are responsible for the swapon command. According to the how-to at [http://tldp.org/HOWTO/Linux+FreeBSD-3.html](http://tldp.org/HOWTO/Linux+FreeBSD-3.html) I have to put the following line into one of these files just before swapon -a
```

awk -- '/swap/ && ($1 !~ /#/) { system("mkswap "$1"") }' /etc/fstab

```

Does Ubuntu use any other scripts responsible for mounting swap?

I'm guessing that instead of changing anything I could just add something like the following to the top of the script:

```

swap_find_mk() {
awk -- '/swap/ && ($1 !~ /#/) { system("mkswap "$1"") }' /etc/fstab
}
swapon() {
swap_find_mk && swapon }

```

After analyzing the two scripts it seems that this would replace all instances of swapon with that small tidbit of code and leave the flags that each script uses untouched. What I'm confused about is whether or not I need to edit both of the scripts or only one.

Please help.

---

