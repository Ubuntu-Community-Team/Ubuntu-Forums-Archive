---
title: "Dead installation, recovering packages"
date: 2009-12-12
forum: General Help
---

### Post by yoman82 on 2009-12-12
Ok, my Ubuntu install fails to boot when I upgraded to 10.04. I'm going to reinstall 9.10, but I'd like to back up the packages I have installed on the desktop. But since it fails to boot, I have to back it up from the Live CD. Know any way too?
Thank you so much.

---

### Post by mac9416 on 2009-12-12
Hey yoman82,

I'm not sure how well this will work since you just finished upgrading, but any package files APT has downloaded are kept in /var/cache/apt/archives. You can copy those to a flash drive and copy them back into that directory once you have reinstalled. That could save you some time and bandwidth.

Good luck!

---

### Post by slakkie on 2009-12-12
You could try to boot from a liveCD and enter your 10.04 install via a chrooted environment.

I've written a script that does all the magic for you:

[http://blog.opperschaap.net/2009/11/16/chroot-with-upstart/](http://blog.opperschaap.net/2009/11/16/chroot-with-upstart/)

When you have entered the chroot, do 

```

dpkg --get-selections > $HOME/dpkg.list

```
When you have installed karmic simple do:

```

sudo dpkg --set-selections < $HOME/dpkg.list
sudo apt-get dselect-upgrade

```

---

