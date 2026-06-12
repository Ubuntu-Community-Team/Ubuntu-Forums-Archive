---
title: "Problem with Grub2"
date: 2011-11-28
forum: General Help
---

### Post by freelancercs on 2011-11-28
Hi!

I have a serious problem with Grub2. 

I usually turn off my notebook for the night and every morning I have to restore Grub2 by using live CD...What's the problem? I really don't know how solve this situation...

Thank you!

---

### Post by crazy bird on 2011-11-28
Check this wiki about Grub2: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by maverickaddicted on 2011-11-28
> **freelancercs said:**
> Hi!

I have a serious problem with Grub2. 

I usually turn off my notebook for the night and every morning I have to restore Grub2 by using live CD...What's the problem? I really don't know how solve this situation...

Thank you!


Are you running following commands after booting up to Ubuntu

```

sudo grub-install --recheck /dev/sda
OR
sudo grub-install /dev/sda

``````
sudo update-grub 
```

If not, then you should.

---

### Post by freelancercs on 2011-11-28
> **maverickaddicted said:**
> Are you running following commands after booting up to Ubuntu

```

sudo grub-install --recheck /dev/sda
OR
sudo grub-install /dev/sda

``````
sudo update-grub 
```

If not, then you should.

Yes, I ran either sudo grub-install /dev/sda and sudo update-grub2

---

### Post by maverickaddicted on 2011-11-28
May be try to reinstall the Grub2 bootloader. After booting normally to Ubuntu, do this-

```
sudo apt-get purge grub grub-pc grub-common
sudo apt-get install grub-common grub-pc
sudo update-grub
```

If that doesn't resolve your problem, look at this forum, it has all the information -

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

