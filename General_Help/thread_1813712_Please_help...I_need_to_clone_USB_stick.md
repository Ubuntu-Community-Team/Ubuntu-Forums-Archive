---
title: "Please help...I need to clone USB stick"
date: 2011-07-28
forum: General Help
---

### Post by muharem84 on 2011-07-28
I have linux installation which is on USB flash drive...there are two partitions.
Can someone tell me how to clone it to another USB. I tried manualy   creating partitions on new flash drive and manualy copyng files but this   doesn't work. Please, can someone help me with this?

---

### Post by timgood on 2011-07-28
A utility called ddrescue is your friend. Check this [link]("http://dimitar.me/clone-disk-drives-with-ubuntu/"). As you are not cloning your hard drive, you will not need to boot into a live cd session, but you will need to install ddrescue.

```
sudo apt-get install ddrescue
```

Hope this helps.

---

### Post by lmarmisa on 2011-07-28
Try to use the command **dd **for cloning your USB stick.

For example, if your source device is **/dev/sdb** and the target is **/dev/sdc** you could type this command:

```

sudo dd if=/dev/sdb of=/dev/sdc conv=sync,noerror bs=1M

```

---

