---
title: "trouble with the 'mount' command"
date: 2009-12-08
forum: General Help
---

### Post by Koalano on 2009-12-08
Hi friends,

I have a partition, /dev/sda4, and I want to mount that partition to /data, and here is what I did:
```
sudo mkdir /data
sudo mount /dev/sda4 /data
```After mounting, if I want to create any new folders/files in that partition, I have to be root. Is there any way to do those things without root privilege? I just want to access the newly mounted partition as a normal folder (I want it to be like every normal folder, such as the ones in /home directory).

Thanks in advance!

---

### Post by Sam on 2009-12-08
Which filesystem is in /dev/sda4 ?

---

### Post by Koalano on 2009-12-08
> **Sam said:**
> Which filesystem is in /dev/sda4 ?

I'm sorry for not providing enough information. It's ext3.

---

### Post by Sam on 2009-12-08
It sounds like the owner of /dev/sda4 is not you (or the permissions are to restrictive). If you wish to claim ownership of the drive, run this when mounted:```
sudo chown -R `whoami`:`whoami` /data && find /data -type d -exec chmod 755 {} \; && find /data -type f -exec chmod 644 {} \;
```

---

### Post by Koalano on 2009-12-08
> **Sam said:**
> It sounds like the owner of /dev/sda4 is not you (or the permissions are to restrictive). If you wish to claim ownership of the drive, run this when mounted:```
sudo chown -R `whoami`:`whoami` /data && find /data -type d -exec chmod 755 {} \; && find /data -type f -exec chmod 644 {} \;
```

Thank you for your reply, but that partition is a new one which I have just created from the unpartitioned space of my hard drive. It is totally empty. I just want an instruction to make that new-and-empty partition accessible (readable/writeable) without being root. 

Regards,

Koalano.

---

### Post by Sam on 2009-12-08
Well, that command does the job.

---

### Post by Koalano on 2009-12-08
> **Sam said:**
> Well, that command does the job.

Yeah, thank you very much. It works like a charm.

---

