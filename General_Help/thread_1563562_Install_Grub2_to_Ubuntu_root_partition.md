---
title: "Install Grub2 to Ubuntu root partition"
date: 2010-08-29
forum: General Help
---

### Post by jpcanaverde on 2010-08-29
Hi. I currently have Grub2 in my MBR, but I installed Mac OS X and decided I want to use Chameleon instead (I know Grub can boot OS X, but I like Chameleon more, and besides that, Grub only booted OS X one time, the next time I restarted it said it didn't find a module or something.)

But Chameleon doesn't recognize Ubuntu, because it doesn't have a bootloader installed. So, I have to install grub to the Ubuntu root's partition.

I identified the partition mounted as "/" with the "df" command. It was /dev/sda5.

So, I typed:

```
sudo grub-install /dev/sda5
```

It returned:

```


Trying to install GRUB to a partition instead of MBR. This is a bad idea.

/usr/sbin/grub-setup: warn: Can't embed. GRUB can only be installed in this configuration using block lists. However, block lists are unreliable and its use is discouraged.

/usr/sbin/grub-setup: error: if you really want to block lists, use --force.


```

So I got a bit scared, and I don't know what to do. So decided to ask for your help...

Can you give me some advice, please?

Thanks,

JPCanaverde

---

