---
title: "rescue mode now totally useless"
date: 2011-12-31
forum: General Help
---

### Post by sonicb00m on 2011-12-31
I am trying to enter rescue mode to fix a problem with my partition.

I want to disable a line in fstab but I can't mount the drives because it just hangs when I select the option to  mount them. If i drop to just a root shell it goes to read only mode which is absolutely no use to anyone! Why the hell does it do this? And how do I solve it without booting a live cd?

---

### Post by galvatron408 on 2012-01-01
you should enter single user rw mode (not rescue mode).

---

### Post by rsvancara on 2012-01-01
Have you tried remounting the drive like this:

mount -o remount,rw /dev/somedevice

--
[Know Your Linux?]("http://www.knowyourlinux.com/")

---

### Post by sonicb00m on 2012-01-01
> **galvatron408 said:**
> you should enter single user rw mode (not rescue mode).

I don't have any other option in grub other than "recovery mode" and none of the menu's thereon specify this.

---

### Post by sonicb00m on 2012-01-01
> **rsvancara said:**
> Have you tried remounting the drive like this:

mount -o remount,rw /dev/somedevice

--
[Know Your Linux?]("http://www.knowyourlinux.com/")

Yes that worked. Why isn't this done by default anymore? Thank you!

---

### Post by rsvancara on 2012-01-01
I had ran into the same problem just a few days ago.  I am glad this helped.

---

### Post by sonicb00m on 2012-01-02
> **rsvancara said:**
> I had ran into the same problem just a few days ago.  I am glad this helped.

It's really annoying. I am bit disappointed with some of the changes in Ubuntu the last year. It feels it's getting more like windows with this "We know best" attitude and constant removal or hiding of features.

---

