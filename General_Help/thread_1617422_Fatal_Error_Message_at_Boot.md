---
title: "Fatal Error Message at Boot"
date: 2010-11-09
forum: General Help
---

### Post by cottfcfan on 2010-11-09
After installing Maverick i386, I'm noticing at boot just before the plymouth theme a "Fatal Error" message, it flashes up so quick I don't have time to read it all.
 Boot continues and everything appears fine.
 How can i retrieve the message so I know what the problem is?

---

### Post by Hippytaff on 2010-11-09
The error should be in your boot logs
```

cd var/logs/

```
and
```

ls

```
to list the logs in that diretory.

---

### Post by ajgreeny on 2010-11-09
> **Hippytaff said:**
> The error should be in your boot logs
```

cd /var/log/

```and
```

ls

```to list the logs in that diretory.
Note the errors in the above post from Hippytaff, edited and changed in my quote.

It may help to read the boot.log with ```
cat boot.log
```

---

### Post by Hippytaff on 2010-11-09
> **ajgreeny said:**
> Note the errors in the above post from Hippytaff, edited and changed in my quote.
 
It may help to read the boot.log with ```
cat boot.log
```
 
oops - typo.
 
and yes
```

cat /var/log/boot.log

```
would be an easier option, though I wasn't on my ubuntu box to check and couldn't remember the name boot.log without looking. :-s :-)

---

### Post by cottfcfan on 2010-11-09
Thanks for your replies.
I checked the logs but couldn't really find anything.
The installation was from a Linux Format DVD, so I wondered if that was the problem.
 Anyway I've reinstalled with my own copy of Meerkat and the problem seems to have gone away. So I can only assume a dodgy DVD.
 I'll mark this as solved although it's more worked around.

---

### Post by Hippytaff on 2010-11-09
If it was 10.10 from Linux Format it was probably the beta version. I have that magazine too :-)

---

### Post by cottfcfan on 2010-11-09
Hippytaff,
No it was the full version only arrived yesterday, but they've messed a bit with the distro and added some extra stuff, so i'm assuming it has something to do with that. May not be, could be a bad disc or just a bad install, didn't seem to affect the running of it, but i'm paranoid about "Error Messages" so reinstalled now.

---

### Post by Hippytaff on 2010-11-09
> **cottfcfan said:**
> Hippytaff,
No it was the full version only arrived yesterday, but they've messed a bit with the distro and added some extra stuff, so i'm assuming it has something to do with that. May not be, could be a bad disc or just a bad install, didn't seem to affect the running of it, but i'm paranoid about "Error Messages" so reinstalled now.

I need to subscribe, I have to wait another 4 days for my copy - sucks

---

