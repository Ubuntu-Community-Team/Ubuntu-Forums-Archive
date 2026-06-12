---
title: "Permissions problem"
date: 2012-02-24
forum: General Help
---

### Post by geoinc on 2012-02-24
I changed the permissions of the etc directory by mistake and I cannot change the permissions back to root.  When I try it says operation not permitted.  I am running Ubuntu desktop 11.10.

---

### Post by roelforg on 2012-02-24
Boot into the livecd.
Mount the hd to /media/hd
execute:
```

sudo chown root:root -R /media/hd/etc

```

---

### Post by geoinc on 2012-02-24
Thanks for the reply.  How do I mount the hd to /media/hd/etc/ ?

---

### Post by roelforg on 2012-02-24
Try:
```

sudo mkdir -p /media/hd
sudo mount /dev/sda1 /media/hd

```

---

### Post by geoinc on 2012-02-24
I entered the commands.  Now I can't get the system to boot up from the hard drive.

---

### Post by roelforg on 2012-02-24
Give me the error
Also try:
```

sudo chmod root:shadow /media/hd/etc/*shadow

```

---

### Post by geoinc on 2012-02-24
No error. After the BIOS screen it stays black

---

### Post by roelforg on 2012-02-24
> **geoinc said:**
> No error. After the BIOS screen it stays black
Has grub showed itself?
If not, try boot-repair (the wiki has more info).

---

