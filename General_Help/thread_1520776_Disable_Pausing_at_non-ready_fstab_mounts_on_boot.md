---
title: "Disable Pausing at non-ready fstab mounts on boot"
date: 2010-06-30
forum: General Help
---

### Post by swordphsh on 2010-06-30
I have a few entries in fstab such as usb device static mount points, network shares, and truecrypt volumes which are not available at boot (ie drives not plugged in, network share over wireless, etc), but the new boot program in 10.04 stops at each device to inform me they are not ready to mount. 

I'm looking for a way to disable this function or to exempt certain mounts from the rule. 

Thanks in advance.

---

### Post by mikewhatever on 2010-06-30
Remove the unneeded entries, and add 'noauto' options to other ones you tend to have unplugged.

---

### Post by swordphsh on 2010-06-30
Good idea, I didn't think of that, but I'd like to disable the message, if possible, since I have a few things that are network dependent and need to wait for the wifi. It's nice to just mount all once the network is up.

---

### Post by jamessnell on 2010-11-09
Indeed, I'd like to know the same thing. I generally find this particularly annoying on server machines I rarely reboot. Of course, when I do reboot them its remotely and these pauses kill my boot process. It'd help if the pause would auto 'skip' after a (maybe even long) timeout. But regardless, I'd like to put a flag or something in fstab that'll disable said messages.

Any help would be most appreciated.

---

### Post by jamessnell on 2010-11-09
> **jamessnell said:**
> Indeed, I'd like to know the same thing. I generally find this particularly annoying on server machines I rarely reboot. Of course, when I do reboot them its remotely and these pauses kill my boot process. It'd help if the pause would auto 'skip' after a (maybe even long) timeout. But regardless, I'd like to put a flag or something in fstab that'll disable said messages.

Any help would be most appreciated.

What looks like a viable option (to me) is to add the *nobootwait* flag to your mounts in */etc/fstab*. For Example, perhaps something like:

```

/Storage/Volumes/RAID/Music/         /Storage/Interface/Music/         none    bind,auto,user,defaults,nobootwait 0 0

```

Someone helpfully mentioned that on the rather [long discussion regarding this here]("https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/571444").

Of course, I'm still a fan of an auto timeout for these messages too.

---

