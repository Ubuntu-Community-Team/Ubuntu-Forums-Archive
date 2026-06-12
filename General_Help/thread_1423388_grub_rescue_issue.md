---
title: "grub rescue issue"
date: 2010-03-06
forum: General Help
---

### Post by segwar on 2010-03-06
Hi All,
By what I have read, a boot to the "grub rescue>" prompt is a pretty common thing. I have a unique isssue.
 
I am at the Grub Rescue prompt and I have completed the following steps
```

set prefix=(hd0,1)/boot/grub
set root(=(hd0,1)

```
 
After that I am supposed to do the insmod and go into the normal.mod or linux.mod.
The issue here is that the output to the 
```

ls /boot 

```
 
shows me a list of all the initrd and the  vmlinuz files but the output of the command
 
```

ls /boot/grub

```
 
shows me the follwing output
```

/etc/mysql
/etc/mysql/conf.d
/etc/mysql/my.cnf

```
 
and few files in the .usr directory
 
The ls commands gives the follwing output
```

(hd0) (hd0,5) (hd0,1) (hd1) (hd1,1) (fd0)

```
 
only the ls (hd0,1)/boot shows me the list of the vmlinuz and the intrid files.
 
questions
 
1) where are my grub file gone?
2) is there a way for me to rescue/restore them(I have the live cd)?
3) how can I prevent this from happening again?
 
I am on ubuntu 9.04 single OS system.
 
Thanks
 
Segwar.

---

### Post by bobcollard on 2010-03-06
> **segwar said:**
> Hi All,
By what I have read, a boot to the "grub rescue>" prompt is a pretty common thing. I have a unique isssue.
 
I am at the Grub Rescue prompt and I have completed the following steps
```

set prefix=(hd0,1)/boot/grub
set root(=(hd0,1)

```After that I am supposed to do the insmod and go into the normal.mod or linux.mod.
The issue here is that the output to the 
```

ls /boot 

```shows me a list of all the initrd and the  vmlinuz files but the output of the command
 
```

ls /boot/grub

```shows me the follwing output
```

/etc/mysql
/etc/mysql/conf.d
/etc/mysql/my.cnf

```and few files in the .usr directory
 
The ls commands gives the follwing output
```

(hd0) (hd0,5) (hd0,1) (hd1) (hd1,1) (fd0)

```only the ls (hd0,1)/boot shows me the list of the vmlinuz and the intrid files.
 
questions
 
1) where are my grub file gone?
2) is there a way for me to rescue/restore them(I have the live cd)?
3) how can I prevent this from happening again?
 
I am on ubuntu 9.04 single OS system.
 
Thanks
 
Segwar.
```
sudo update-grub
```

---

### Post by segwar on 2010-03-07
HI ,
Thanks for the response,
 
I booted to the live cd and ran an update-grub command. I am still facing the isssue after I reboot.
 
Is there a way to reinstall ubuntu without loosing data? Or any oher way to fix this.
 
Thanks.
 
Segwar

---

### Post by bobcollard on 2010-03-07
> **segwar said:**
> HI ,
Thanks for the response,
 
I booted to the live cd and ran an update-grub command. I am still facing the isssue after I reboot.
 
Is there a way to reinstall ubuntu without loosing data? Or any oher way to fix this.
 
Thanks.
 
Segwar
Back up your home directory then start from scratch.  You could burn it to a CD or DVD if you don't have a separate drive.

---

