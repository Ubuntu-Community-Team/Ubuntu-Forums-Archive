---
title: "10:10: fstab corrupted; no backup. How to rebuild?"
date: 2011-03-14
forum: General Help
---

### Post by XEtedBear on 2011-03-14
My system won't boot because the contents of /etc/fstab, while semantically valid, are not meaningful in my system - neither / or /home is defined, for example.

For this reason too fsck will not run.

The grub menu displays OK.

How do I rebuild fstab?

How do I get permission to change any files on my system when using the Live-CD? Right now all attempts are stopped with a 'permission denied' message.

---

### Post by Lars Noodén on 2011-03-14
Boot a rescue CD or live CD and try looking at the partitions with parted or gparted.  How complex is your partitioning scheme?

---

### Post by oldfred on 2011-03-14
Often liveCD needs sudo but then no password.

a bad fstab would not prevent fsck from running.

Can you post your fstab?

This is mine:

```
# / was on /dev/sda5 during installation
UUID=f2e3d649-d0cf-4ac8-b617-b7842dcbc011 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=305abe8d-52fd-4ef1-be0a-9dedc417a1be none            swap    sw              0       0

```

To see your UUIDs 
```

sudo blkid
```

---

### Post by XEtedBear on 2011-03-15
> **oldfred said:**
> 

a bad fstab would not prevent fsck from running.


You are quite right and I am quite wrong.

I have been making ignorance-lead guesses about the cause of the failure of my system to boot. Having booted from my install CD what I thought was  my installed system fstab was only the (semantically correct) fstab being used by the 'live' installation.

After some further painful hours if similar low-quality guesses I have now found that the cause of the boot failure was a corruption in my '/' partition filesystem. Booting a Gparted CD and running 'check and correct' against that parition fixed the issues and allowed me to boot normally to Ubuntu. And then I was able to see my installed fstab and find - just like you suspected - that it has no problem (aside from missing one entry which I can easily fix).

So, thanks for the advice. I wish  I was better informed about these internals of Linux - but actually I need the time for using it, not 'nursing' it!

As to why the '/' partition acquired a file system error - who knows?

---

