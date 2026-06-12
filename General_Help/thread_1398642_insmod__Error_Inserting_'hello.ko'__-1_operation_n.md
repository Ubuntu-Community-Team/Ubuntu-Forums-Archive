---
title: "insmod : Error Inserting 'hello.ko' : -1 operation not permitted"
date: 2010-02-04
forum: General Help
---

### Post by kart_ram on 2010-02-04
**:(**

Hi all , 

I am new to Linux . Working on module insertion . Getting the above mentioned error using a compiled hello world program. Am using 2.6.28-11 version of ubuntu. Did little bit of research to overcome this error. Also tried using modprobe but was not successful. Looking forward to some guidance/help . Thanks in advance !

modprobe version is :
 module-init-tools version 3.7-pre9
 Used this command :
 modprobe -v hello.ko
 FATAL: Module hello.ko not found.
 
 /* hello.c */
#include <linux/module.h> /* Needed by all modules */
#include <linux/kernel.h> /* Needed for KERN_INFO */
int init_module(void)
{
         printk(KERN_INFO "Hello world 1.\n");
          // A non 0 return means init_module failed; module can't be loaded.
          return 0;
}
void cleanup_module(void)
{
         printk(KERN_INFO "Goodbye world 1.\n");
}

---

### Post by cariboo on 2010-02-05
You need to be root to insert a module:

```
sudo modprobe -v hello.ko
```

good luck

---

### Post by adam814 on 2010-02-05
I commend you for your bravery.  Building kernel modules isn't something I would have tried while learning Linux.   I assume that's what you're doing since it would be a lot easier just to write a C program for userspace to do the same thing.

---

### Post by kart_ram on 2010-02-05
> **cariboo907 said:**
> You need to be root to insert a module:

```
sudo modprobe -v hello.ko
```good luck


Hi ,
I tried :
sudo modprobe -v hello.ko
got this error :
**sudo: must be setuid root**

I searched to fix this error of setuid . Someone had suggested to try :
chown root:root /usr/bin/sudo
chmod 4111 /usr/bin/sudo 
Got this error :
**chown: changing ownership of `/usr/bin/sudo': Operation not permitted.** However secind command dint give any error.
There's sudo in /usr/bin but it's got a lock on it. someone has suggested to login into safemode and then perform some operations. But am not sure if i should take that advice, as i have very less time and dont want to mess up the system. Please refer this link for more info on above information.
[http://ubuntuforums.org/showthread.php?t=251358](http://ubuntuforums.org/showthread.php?t=251358)

  
 > **adam814 said:**
> I commend you for your bravery. Building kernel modules isn't something I would have tried while learning Linux. I assume that's what you're doing since it would be a lot easier just to write a C program for userspace to do the same thing.

You mean write a c program to do insmod ?? Sorry i dint get you sir.


@all : Thanks in advance for your time and consideration. Please guide/help.

---

### Post by adam814 on 2010-02-05
I just meant the standard C "hello world" program is a lot easier to write and run than a kernel module that does it.  It wouldn't involve modprobe or insmod, you'd just build an executable and run it.

I wouldn't change the ownership/permissions on system executables just because another thread somewhere says to.  At best it could be a security risk and at worst you may "lock yourself out" of running them.  Besides, it looks like it should have been "chmod 4755 /usr/bin/sudo" instead.  That would set it to the "default" permissions.

P.S. I think if you don't have hello.ko in the standard kernel module directories modprobe won't load it.  You could specify the path with insmod and it should load (you'll also need to use sudo).

---

