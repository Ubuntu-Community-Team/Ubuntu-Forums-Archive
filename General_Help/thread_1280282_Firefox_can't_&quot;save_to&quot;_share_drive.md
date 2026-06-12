---
title: "Firefox can't &quot;save to&quot; share drive"
date: 2009-10-01
forum: General Help
---

### Post by tripler on 2009-10-01
Ubuntu 9.04, Firefox 3.0.14. When I chose "save to" in Firefox I can't see my windows share drive (external HD plugged into an w2k machine). I can see it fine through Places. On XP (dual boot on the Ubuntu machine)  I can see the share ok when saving from Firefox. Is there a way to make Firefox see it in Ubuntu?

---

### Post by Ubu-freak on 2009-10-01
Did you mount the drive you wish to save to?

---

### Post by tripler on 2009-10-01
> **Ubu-freak said:**
> Did you mount the drive you wish to save to?

I can see it in Places under Network and can access it from there so it must be mounted. Is there another way I need to mount it?

---

### Post by Ubu-freak on 2009-10-02
sorry then i don't know

---

### Post by oldfred on 2009-10-02
I think you need a permanent mount.

Try installing pysdm from the repos.

Or manually edit fstab:
see this for fstab info:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

