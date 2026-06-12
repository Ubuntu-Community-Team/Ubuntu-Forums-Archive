---
title: "Problem mounting nested nfs location"
date: 2009-11-16
forum: General Help
---

### Post by tarekeldeeb on 2009-11-16
Hello all,

Straight to the problem ..

I have ~/Net/share as empty folder tree

I have this in my fstab
```
192.168.0.1:/home/tarek/Net    /home/tarek/Net   nfs    rsize=8192,wsize=8192,timeo=14,intr
192.168.0.1:/home/share    /home/tarek/Net/share   nfs    rsize=8192,wsize=8192,timeo=14,intr
```

where the remote server is 192.168.0.1 with its /home exported

The problem is:
Only ~/Net is mounted at start up.
I have to do manual 
```
sudo mount -a
```
to mount the share directory.
Not all users are sudoers, so this makes a problem!!

Can any1 solve my situation?

I still prefer the 'share' to be inside 'Net'

Thanks in advance,
Tarek

---

### Post by Giblet5 on 2009-11-16
> **tarekeldeeb said:**
> Hello all,

Straight to the problem ..

I have ~/Net/share as empty folder tree

I have this in my fstab
```
192.168.0.1:/home/tarek/Net    /home/tarek/Net   nfs    rsize=8192,wsize=8192,timeo=14,intr
192.168.0.1:/home/share    /home/tarek/Net/share   nfs    rsize=8192,wsize=8192,timeo=14,intr
```

where the remote server is 192.168.0.1 with its /home exported

The problem is:
Only ~/Net is mounted at start up.
I have to do manual 
```
sudo mount -a
```
to mount the share directory.
Not all users are sudoers, so this makes a problem!!

Can any1 solve my situation?

I still prefer the 'share' to be inside 'Net'

Thanks in advance,
Tarek

I think the default option includes "noauto", so you should try adding "auto" to the options.

```
192.168.0.1:/home/tarek/Net    /home/tarek/Net   nfs    auto,rsize=8192,wsize=8192,timeo=14,intr
192.168.0.1:/home/share    /home/tarek/Net/share   nfs    auto,rsize=8192,wsize=8192,timeo=14,intr
```

---

### Post by tarekeldeeb on 2009-11-16
> **Giblet5 said:**
> I think the default option includes "noauto", so you should try adding "auto" to the options.


Yes !

It works ..

But what does auto/noauto mean anyways?

---

### Post by Giblet5 on 2009-11-16
"noauto" means don't automount this entry - wait for mount -a. That's part of the "default" option stack. Some required filesystems (eg /) will mount regardless.

"auto" means automount this entry.

```
man mount
``` will show you the manual for mount and it includes lots of information on the commonly used options.

You might want to look at the "user" option, too.

Oddball filesystem types may have additional options as well, and mount can pass those options which it does not interpret to that filesystem's driver.

---

### Post by tarekeldeeb on 2009-11-16
thanks  a lot for this fruitful info

:)

---

