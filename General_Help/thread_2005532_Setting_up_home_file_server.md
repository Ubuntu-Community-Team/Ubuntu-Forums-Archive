---
title: "Setting up home file server"
date: 2012-06-17
forum: General Help
---

### Post by Jaymie on 2012-06-17
Hi,

I am looking to turn an old PC in the file sharing / server pc so the PC's in my household can share files between each other.

I am currently looking into FreeNAS, but am now wondering about ubuntu.

I have used ubuntu desktop version before and I know that ubuntu has a server version but i like the user interface so I can see what im looking at.

Is ubuntu something I could use?

Thanks,

Jaymie. :)

---

### Post by Bobhuber on 2012-06-17
> **Jaymie said:**
> Hi,

I am looking to turn an old PC in the file sharing / server pc so the PC's in my household can share files between each other.

I am currently looking into FreeNAS, but am now wondering about ubuntu.

I have used ubuntu desktop version before and I know that ubuntu has a server version but i like the user interface so I can see what im looking at.

Is ubuntu something I could use?

Thanks,

Jaymie. :)
Ubuntu desktop with apache2 loaded for your server. Best of both worlds.

---

### Post by Mopar1973Man on 2012-06-17
If so them you might want to follow this install...
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Just skip the MySQL and PHP...

---

### Post by dcottingham on 2012-06-17
Not clear what services you want your server to provide. You mention sharing files -- did you want to share files with Windows machines, in which case you want SMB, or share files with Apples, in which case you want AFP, or other Linux/Unix machines, in which case you might want NFS, or were you thinking of something else?

---

### Post by Jaymie on 2012-06-18
> **dcottingham said:**
> Not clear what services you want your server to provide. You mention sharing files -- did you want to share files with Windows machines, in which case you want SMB, or share files with Apples, in which case you want AFP, or other Linux/Unix machines, in which case you might want NFS, or were you thinking of something else?

Hi,

I am wanting to share files with Windows machines.

---

### Post by dcottingham on 2012-06-18
OK, so the answer to your original question is, yes, you can do this with ubuntu desktop. You need to install and configure samba, which implements shared folders for Windows machines. (And if I recall correctly other things, like printer sharing.) I believe the Ubuntu package name you want is "samba4".

---

### Post by Morbius1 on 2012-06-18
> **dcottingham said:**
>  I believe the Ubuntu package name you want is "samba4".
Don't mean to interrupt but I would not install Samba4. From synaptic:
> These packages contain snapshot versions of Samba 4, the next-generation version of Samba. These should be considered _experimental_, and should not be used in production.
Samba4 is at an alpha state. Given my age and the pace of development it may not get to a beta state in my lifetime ;)

Non Samba4 packages are fine.

---

### Post by dcottingham on 2012-06-18
I see what you mean. Yes, belay that "samba4". I think the package you want is "samba".

---

