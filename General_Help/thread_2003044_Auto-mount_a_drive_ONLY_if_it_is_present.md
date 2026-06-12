---
title: "Auto-mount a drive ONLY if it is present"
date: 2012-06-13
forum: General Help
---

### Post by lethalfang on 2012-06-13
I edited the /etc/fstab to auto-mount a drive. The problem is that, when the drive is not present, my system refuses to boot until the drive is found. 
How do I auto-mount a drive only if it is found, but continue booting if it isn't found?

Thanks.

---

### Post by kanikilu on 2012-06-13
A quick search ([https://www.google.com/search?q=conditional+fstab+mounts](https://www.google.com/search?q=conditional+fstab+mounts)) doesn't bring up good news. I'm not really sure where to go from here exactly, but I'd *think* one way to achieve a similar result would be to create a simple bash script to see if the drive exists, and then mount it. If that works, then it's just a matter of adding that script to your startup.

Something like: ```
#!/bin/bash
if [ -e /dev/disk/by-uuid/08996281-7fcf-45eb-9fc5-272c810d9fd2 ]
then
    mount -t fstype /dev/disk/by-uuid/08996281-7fcf-45eb-9fc5-272c810d9fd2 /mnt/mountpoint
fi
```

Obviously, you'd need to put in your real UUID, mountpoint, fstype and any other options you need to mount it.

I haven't tested this, and maybe someone can chime in with a better solution, but I don't see why it wouldn't work...

---

### Post by lethalfang on 2012-06-13
> **kanikilu said:**
> A quick search ([https://www.google.com/search?q=conditional+fstab+mounts](https://www.google.com/search?q=conditional+fstab+mounts)) doesn't bring up good news. I'm not really sure where to go from here exactly, but I'd *think* one way to achieve a similar result would be to create a simple bash script to see if the drive exists, and then mount it. If that works, then it's just a matter of adding that script to your startup.

Something like: ```
#!/bin/bash
if [ -e /dev/disk/by-uuid/08996281-7fcf-45eb-9fc5-272c810d9fd2 ]
then
    mount -t fstype /dev/disk/by-uuid/08996281-7fcf-45eb-9fc5-272c810d9fd2 /mnt/mountpoint
fi
```

Obviously, you'd need to put in your real UUID, mountpoint, fstype and any other options you need to mount it.

I haven't tested this, and maybe someone can chime in with a better solution, but I don't see why it wouldn't work...

Well, I think that's fine solution. Thanks.

---

### Post by LewisTM on 2012-06-13
Add the 'nobootwait' mount option to the concerned fstab lines

Ubuntu manpage **fstab**
> The  mountall(8)  program  that  mounts  filesystem  during  boot  also recognises additional options that the ordinary mount(8) tool does not.These  are:  ``bootwait''  which  can  be applied to remote filesystems mounted outside of /usr or /var, without which  mountall(8)  would  not hold up the boot for these; ``**nobootwait**'' which can be applied to non- remote filesystems to explicitly instruct mountall(8) not  to  hold  up the boot for them [...]

Cheers!

---

### Post by matt_symes on 2012-06-13
Hi

> **LewisTM said:**
> Add the 'nobootwait' mount option to the concerned fstab lines

^^^ This. 

I use it on my media server. It works a treat.

Kind regards

---

### Post by dcstar on 2012-06-14
> **LewisTM said:**
> Add the '**nobootwait**' mount option to the concerned fstab lines
.........


I can confirm that the **nobootwait** option works well, and I also use the **noatime** option to reduce unnecessary disk writes.

I use both of these on an external SATA drive that I only power on at a specific day to backup to using Unison, and it all works fine.

---

### Post by lethalfang on 2012-06-26
> **matt_symes said:**
> Hi



^^^ This. 

I use it on my media server. It works a treat.

Kind regards

Thanks.

---

### Post by dcstar on 2012-06-27
> **lethalfang said:**
> Thanks.

Then MARK the thread!

---

