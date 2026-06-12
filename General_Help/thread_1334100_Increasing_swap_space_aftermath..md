---
title: "Increasing swap space aftermath."
date: 2009-11-22
forum: General Help
---

### Post by A_Nonny_Moose on 2009-11-22
9.10

I added a new swap file, put it in the fstab table with its UUID, executed the **swapon** command and did not get the improvement I expected.

Yes, I made sure the space was formatted the same as the existing file, and so on.

Am I missing something?  Is there a method to turn on virtual paging?

---

### Post by nikhilbhardwaj on 2009-11-22
[http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/](http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/)

---

### Post by SPr on 2009-11-22
> **A_Nonny_Moose said:**
> I added a new swap file, put it in the fstab table with its UUID

So you created swap partition rather than a swap file?
Are you certain the UUID is correct?
```

sudo blkid|grep swap

```
will give details. Use this to check /etc/fstab.

```

sudo swapon -a

```
will turn it on if /etc/fstab points to the correct partition.

---

