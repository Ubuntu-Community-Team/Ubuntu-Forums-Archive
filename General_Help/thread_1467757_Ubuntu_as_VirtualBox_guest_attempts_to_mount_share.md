---
title: "Ubuntu as VirtualBox guest attempts to mount shared folders twice at startup"
date: 2010-05-01
forum: General Help
---

### Post by jlebar on 2010-05-01
Moved to virtualization forum: [http://ubuntuforums.org/showthread.php?p=9207703](http://ubuntuforums.org/showthread.php?p=9207703)

I just upgraded my Ubuntu VirtualBox guest to Lucid.

My host machine shares two folders with the guest.  I have them listed in my /etc/fstab so they're automatically mounted:

share /mnt/share vboxsf defaults 0 0

For some reason, it looks like Ubuntu attempts to mount these shared folders twice.  The first time, the mount doesn't succeed, but the second time, it does, so by the time I actually log in, the shares work properly.

Karmic would just print an error message at boot, but now Lucid makes me press a key to continue booting when the mount fails.

Ideally, I'd like to figure out how to make the first mount attempt work properly.  But if that's complicated, just disabling Lucid's prompt would make me happy.

Any ideas how I can go about accomplishing this?

Thanks.

---

### Post by dcstar on 2010-05-01
> **jlebar said:**
> I just upgraded my Ubuntu VirtualBox guest to Lucid.

My host machine shares two folders with the guest.  I have them listed in my /etc/fstab so they're automatically mounted:

share /mnt/share vboxsf defaults 0 0

For some reason, it looks like Ubuntu attempts to mount these shared folders twice.  The first time, the mount doesn't succeed, but the second time, it does, so by the time I actually log in, the shares work properly.

Karmic would just print an error message at boot, but now Lucid makes me press a key to continue booting when the mount fails.

Ideally, I'd like to figure out how to make the first mount attempt work properly.  But if that's complicated, just disabling Lucid's prompt would make me happy.

Any ideas how I can go about accomplishing this?

Thanks.

Look in the Virtualization forum for VM issues.

---

