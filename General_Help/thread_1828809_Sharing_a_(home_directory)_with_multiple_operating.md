---
title: "Sharing a (home directory?) with multiple operating systems?"
date: 2011-08-19
forum: General Help
---

### Post by ClientAlive on 2011-08-19
I'm on my way to starting a (virtual machine farm? is that what you would call it?) and I've been thinking about how to maximize disk space. If I were to just install distros (as virtual machines) in the regular way then they'd all have to have their own piece of the disk carved out (for each one of them). That would mean, with a fixed disk space, that I could not install as many that way as if I looked for other options. One thing that I though about is if I can have all of them share the same home directory. Then maybe you give the home directory a handsome chunk of space but every distro only takes a small amount to be on there and then you can get dramatically more machines on the system (right?).

Another thing that occurred to me would be to share the same kernel amongst many distros. This also would be a way to economize disk space.

In that same vein, perhaps there are many other programs that are shared amongst the various distros. Isn't there some way to identify all the commonalities so you can just have a single instance of anything that is used in two or more distros?? Then whey you start a particular machine the system merely combines all the right things for that distro to be what it's supposed to.

Can't you do that? What would some of these things be called that a guy might learn about them and even employ them? Can anyone steer me straight here?

Thanks in advance for your help.

---

### Post by spiky001 on 2011-08-19
Shareing the same home is not a good idea, Swap can be shared

---

### Post by Wim Sturkenboom on 2011-08-19
Yes it can be done but configurations might influence each other. It's easiest to have somewhere a partition that you can share between the distros and dump all your data on there. And keep the real home partitions separate; they don't have to be that big in that case and can even be directories instead of partitions.

Also pay attention to user IDs. Ubuntu starts at 1000 for non-system users and other distros can start at 500. Result is that the shared information (also applies to home directory) can not be accessed by one of the two unless you take precautions when you create the users.

---

### Post by fdrake on 2011-08-19
> **ClientAlive said:**
> I'm on my way to starting a (virtual machine farm? is that what you would call it?) and I've been thinking about how to maximize disk space. If I were to just install distros (as virtual machines) in the regular way then they'd all have to have their own piece of the disk carved out (for each one of them). That would mean, with a fixed disk space, that I could not install as many that way as if I looked for other options. One thing that I though about is if I can have all of them share the same home directory. Then maybe you give the home directory a handsome chunk of space but every distro only takes a small amount to be on there and then you can get dramatically more machines on the system (right?).

Another thing that occurred to me would be to share the same kernel amongst many distros. This also would be a way to economize disk space.

In that same vein, perhaps there are many other programs that are shared amongst the various distros. Isn't there some way to identify all the commonalities so you can just have a single instance of anything that is used in two or more distros?? Then whey you start a particular machine the system merely combines all the right things for that distro to be what it's supposed to.

Can't you do that? What would some of these things be called that a guy might learn about them and even employ them? Can anyone steer me straight here?

Thanks in advance for your help.

i wouldn't share the home directory with other os system since in the home directory are present your configuration files, and those files my be different or create problem with other distros. You may be able to share your Desktop folder or anether media-data folder with no configuration files involved. Just create a new partition(possibly ext3) and mont that partition in the ~/Desktop mount point . Apply the mountpoint to all os and you are all set.

---

