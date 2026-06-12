---
title: "Since upgrade to 10.04 I cant shut down my computer"
date: 2010-11-06
forum: General Help
---

### Post by zonemikel on 2010-11-06
I've upgraded several times before, this time everything seems great but when I go to shut down my computer it just hangs with the xubuntu logo (little mouse). I'm using the gdm desktop not xubuntu's desktop. I've changed between them a few times (a long time ago).

if i switch to different consoles i can see something about "unmounting weak filesystems" 

It does eventually shut down but it takes like 10+ minutes. I've tried all the acpi force and all that stuff. 

```
michael@ubuntu:~$ cat /etc/default/grub 
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"
GRUB_CMDLINE_LINUX="acpi=force"
michael@ubuntu:~$ cat /etc/issue
Ubuntu 10.04.1 LTS \n \l

michael@ubuntu:~$ 
```

---

### Post by sikander3786 on 2010-11-06
Can you simply press Esc key at the Xubuntu log screen and see what is happening behind the scenes?

---

### Post by zonemikel on 2010-11-07
> **sikander3786 said:**
> Can you simply press Esc key at the Xubuntu log screen and see what is happening behind the scenes?

Yes these are the last few lines, i havent stared at the screen for 10 minutes to see what it says just before it shuts down though. 

```

   killall5: omit pid buffer size 16 exceeded!
. . .       
 * Unmounting weak filesystems...       

```

I cant copy paste but thats what i wrote down

---

