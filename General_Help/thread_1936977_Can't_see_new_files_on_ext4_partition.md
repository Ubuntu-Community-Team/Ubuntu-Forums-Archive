---
title: "Can't see new files on ext4 partition"
date: 2012-03-07
forum: General Help
---

### Post by JebusWankel on 2012-03-07
This is quite the unusual phenomenon indeed. When I mount my home partition from windows or a live cd, I get a snapshot of that partition from several months ago. That is to say it contains files I deleted months ago, but not any files from the last several months. When I boot up ubuntu though, it's perfectly normal. The newest files I can find have a modification date of October 5.

What is going on here?

---

### Post by cryptotheslow on 2012-03-07
Probably the most likely explanation is that you encrypted your home directory at some point around that time.

So when you log into Ubuntu normally your encrypted home directory is mounted but when accessing the disk from windows / liveCD you see the older contents because the encrypted home is not mounted to obscure them from view.

When logged into Ubuntu normally open a Terminal and execute the command:
```
mount
```

If you have an encrypted home directory you should see a result along the lines of:
```
/home/cryptouser/.Private on /home/cryptouser type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=fa0516369a9d12dd,ecryptfs_fnek_sig=70a90eae5e38d112)
```

where "cryptouser" will be your username on the machine.

---

### Post by JebusWankel on 2012-03-08
Thanks, that's exactly what happened.

---

