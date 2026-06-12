---
title: "problems mounting"
date: 2006-06-12
forum: General Help
---

### Post by blue cube on 2006-06-12
im having problems mounting my windows shares on my server..
i had no problems with hoary or breezy, but this time it doesnt seem to want to fly and ive tried a million things

this is what the line in my fstab looks like:

> //10.11.0.1/apps    /media/apps smbfs  credentials=/root/.smbcredentials,dmask=777,fmask=777  0    0

then i run mount -a to try to mount the new line and this is what i get:

> root@slappy:~# mount -a
mount: wrong fs type, bad option, bad superblock on //10.11.0.1/apps,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


any ideas? im lost on this.

i run dmesg | tail and the error is:

> [4295092.023000] smbfs: mount_data version 1684370019 is not supported


---

### Post by grooverider on 2006-06-12
check if u have mount.smbfs installed

---

### Post by blue cube on 2006-06-12
[QUOTE=grooverider]check if u have mount.smbfs installed[/QUOTE]

can you be a little more specific (pretty n00bish here)

---

### Post by taurus on 2006-06-12
Open synaptic (System -> Administration -> Synaptic Package Manager) and at the Search field, type
```

smbfs

```
If you don't have it installed on your machine, then install it by ckicking it...  It will probably make you install samba as well.

---

### Post by blue cube on 2006-06-12
hmm

now i get a different error:

> root@slappy:/home/nick6# mount -a
cli_negprot: SMB signing is mandatory and we have disabled it.
5251: protocol negotiation failed
SMB connection failed


---

### Post by taurus on 2006-06-12
See if you can mount it by first before you place it in /etc/fstab!

---

### Post by blue cube on 2006-06-12
same error

i am completely confused by this

---

### Post by blue cube on 2006-06-13
bump

---

### Post by tronica on 2006-06-13
i use the > mount -t cifs //server/sharename /mnt/server -o user=username,pass=password

---

### Post by blue cube on 2006-06-13
that worked perfectly, ill make a script and have it run on boot  thanks everyone

---

