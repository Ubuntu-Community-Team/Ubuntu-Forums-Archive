---
title: "Encrypted Home Help"
date: 2012-05-31
forum: General Help
---

### Post by TheKingOfComputers on 2012-05-31
Hello,

            After I installed Ubuntu 12.04, I had chosen the option to make an encrypted home folder. I know how to access it (Ctrl + H on the home folder...) but when I enter my encrypted private folder, everything is in "crazy speak" (just a bunch of letters/numbers). I know thats the encryption, but how would I place files in there so they are hidden as well? 

I tried placing a document in there but it didn't get encrypted. It just sat there with normal language. How do I encrypt it? Is it automatically encrypted when I place it there but I just can't see it?

---

### Post by cryptotheslow on 2012-05-31
It sounds like perhaps your encrypted directory is not getting mounted.

Can you post back the output of
```
mount -l
```

---

### Post by TheKingOfComputers on 2012-05-31
Ok....

```
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/home/pete/.Private on /home/pete type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=3f31281f04b65d00,ecryptfs_fnek_sig=7081bbe3e4b926c2)
gvfs-fuse-daemon on /home/pete/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=pete)
```

---

### Post by cryptotheslow on 2012-05-31
Hmm - OK, it is mounted at /home/pete

So when in use files will appear unencrypted to you in that dir. However if you browse into /home/pete/.Private then yes you will see all manner of files and dirs with names starting ECRYPTFS_FNEK_ENCRYPTED.FXYKc.xxxxxxx  etc.

You don't need to put files into .Private to have them encrypted - just put them anywhere in your home directory as you normally would. Once you logout your encrypted home directory is unmounted and no-one can read your files.

To test this out, create another user account and login using it, then browse to /home/pete - you will find no readable files.

---

### Post by TheKingOfComputers on 2012-05-31
Ahhh, I see. Thank you for the help. So this is a secure encryption?

---

### Post by cryptotheslow on 2012-05-31
It is as secure as your password.

It uses the AES encryption cipher which has not been cracked (at least to common knowledge) so the only way for someone to access your encrypted files is by brute-force guessing of your password, which providing it is a reasonably complex password would take an extraordinarily long time.

---

### Post by TheKingOfComputers on 2012-05-31
I see. Yes my password is quite secure, I can assure you that.

---

