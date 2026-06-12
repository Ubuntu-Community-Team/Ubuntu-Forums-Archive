---
title: "Trying to restore pam.d"
date: 2010-04-04
forum: General Help
---

### Post by plane phanatic on 2010-04-04
Hey everyone,
I've been doing a bit of customization on my ubuntu install and have added "auth required pam_fprint.so" to my pam.d file in order to allow fingerprint recognition upon boot. After rebooting, I discovered that my fingerprint reader no longer functions (I get the message "Module is Unknown"). I was wondering how I could remove those lines from the common-auth file. I have tried booting a live CD and typing "gksudo gedit mnt/etc/pam.d/common-auth", but when I try to save, I get the error "Could not find the file /home/ubuntu/mnt/etc/pam.d/common-auth."

---

### Post by SPr on 2010-04-04
> **plane phanatic said:**
> "gksudo gedit mnt/etc/pam.d/common-auth", but when I try to save, I get the error "Could not find the file /home/ubuntu/mnt/etc/pam.d/common-auth."

For a start you have the wrong path. It needs a leading / to make it an absolute path rather than a relative path.

Secondly, are you certain the partition is mounted on /mnt and not a subdirectory of /mnt or /media?
```

mount

```
will tell the truth if you can recognise partition in it's output. If it isn't present it will need to be mounted manually.
```

fdisk -l

```
Identify the partition then
```

mkdir /media/internal
mount /dev/**** /media/internal
gedit /media/internal/etc/.../

```
Change /dev/**** to whatever you see in the output of fdisk -l

Thirdly, you don't say which live CD you're using but I don't think the command needs the gksudo prefix.

---

### Post by plane phanatic on 2010-04-04
It turns out it was mounted under /media rather than /mnt (as you suspected)
Thanks for the help SPr!

---

