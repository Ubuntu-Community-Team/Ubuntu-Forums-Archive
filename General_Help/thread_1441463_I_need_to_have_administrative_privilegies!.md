---
title: "I need to have administrative privilegies!"
date: 2010-03-28
forum: General Help
---

### Post by rva1945 on 2010-03-28
In System/Administration/Users and Groups, my user account properties-user privilegies, the Administer the system is checked (only Send and receive fax and Use tape drives are unchecked).

But when I try to run the KDE partition manager, it warns me that I don't have administrative privilegies, so I will not be able to apply changes.

??

---

### Post by sisco311 on 2010-03-28
That's odd. Please open a terminal & post the output of the 
```
id
```command.

Can you use sudo/pkexec in a terminal?

What is the error message (if any) of:
```
sudo echo
```
and
```
pkexec echo
```?

---

### Post by rva1945 on 2010-03-28
> **sisco311 said:**
> That's odd. Please open a terminal & post the output of the 
```
id
```command.

Can you use sudo/pkexec in a terminal?

What is the error message (if any) of:
```
sudo echo
```and
```
pkexec echo
```?

robert@rvasystem:~$ id
uid=1000(robert) gid=1000(robert) groups=0(root),4(adm),20(dialout),24(cdrom),29(audio),30(dip),44(video),46(plugdev),103(fuse),104(lpadmin),112(netdev),115(admin),120(sambashare),1000(robert)
robert@rvasystem:~$ 

robert@rvasystem:~$ sudo/pkexec
bash: sudo/pkexec: No such file or directory

robert@rvasystem:~$ sudo echo
[sudo] password for robert: 

robert@rvasystem:~$ 

robert@rvasystem:~$ pkexec echo
(a windows pops asking me for password, then:)
robert@rvasystem:~$

---

### Post by moshansky on 2010-03-28
It sounds like your account is on the sudoers list (has administrative privileges that are working.) It sounds to me like the program needs to be run as root. Can you try
gksudo NAME_of partition editor
I Think KDE uses QTparted so it would be....
```

gksudo QTparted

```

---

### Post by rva1945 on 2010-03-28
> **moshansky said:**
> It sounds like your account is on the sudoers list (has administrative privileges that are working.) It sounds to me like the program needs to be run as root. Can you try
gksudo NAME_of partition editor
I Think KDE uses QTparted so it would be....
```

gksudo QTparted

```

Did it but nothing happens

robert@rvasystem:~$ gksudo QTparted
robert@rvasystem:~$ 

in fact a task in the task bar appears with the title Starting Administrative Applicacions but ina few seconds it vanishes

---

