---
title: "fskc on reiserfs"
date: 2006-06-19
forum: General Help
---

### Post by noeluylee on 2006-06-19
I am using Kubuntu 6.06 plus updates and im using ReiserFS parition on my home and root, and EXT3 on /boot

I tried to run
sudo touch /forcefsck
sudo touch /forcefsck.reiserfs
sudo touch /force fsck.reiserfs
 
but it doesnt scan on boot, is there a way to run this fsck? fsck is good on my old kubuntu 5.10 using ext3 partion on both home and root. however on reiserfs it doesnt work. 

Also, I would like to run fsck on reiserfs in every 30 restart, like the old once. 

Please let me know how and what to isnstall to get fsck running again. 

Thanks.

---

### Post by tristan on 2006-06-19
Try using reiserfsck , I think that may sort you out :)

---

### Post by noeluylee on 2006-06-20
What command should i issue? something like sudo touch /force reiserfsck ?

also how could i set that it would scan on after 30 restarts/reboot?

thanks.

---

### Post by [S|G] on 2006-06-20
You can't force a check on reiserfs like you can on ext3. Also, there is no need to do that on a reiserFS volume. From reiserfs FAQ:
```

Why are ReiserFS filesystems not fscked on reboot after a crash?

Because ReiserFS provides journalling of meta-data. After a crash, the consistency of a filesystem is restored by replaying the transaction log.


Can I interactively repair a filesystem that was corrupted (due to an internal bug in the kernel or a to hardware fault)?

man reiserfsck

```

---

