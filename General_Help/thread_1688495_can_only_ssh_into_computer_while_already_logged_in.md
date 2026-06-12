---
title: "can only ssh into computer while already logged in"
date: 2011-02-15
forum: General Help
---

### Post by Gakumerasara on 2011-02-15
I just setup a computer at home with RSA key authentication for SSH (as I always do), but it's not behaving quite like it should.  Specifically, if I've logged into the machine itself, then I can SSH to it from other computers without any trouble.  However, if I restart the computer or logout, then all SSH attempts fail.  I've never had this happen before; I've set up about 6 other computers in the exact same way over the past 2 years without any trouble.  any ideas on what the problem might be?

---

### Post by hawkmage on 2011-02-15
This may seam unrelated but have you changed the default openssl.cnf?

---

### Post by Joe of loath on 2011-02-15
It sounds like your PC is only connecting to the network when logged in, which is how network manager works.

The simplest way is to setup wicd, which runs at boot whether you log in or not.

---

### Post by Iowan on 2011-02-15
> **Joe of loath said:**
> It sounds like your PC is only connecting to the network when logged in, which is how network manager works.It's been awhile... seems like there was another way. If I recall, it had to do with making an interface "available to all users".

---

### Post by Gakumerasara on 2011-02-15
> **hawkmage said:**
> This may seam unrelated but have you changed the default openssl.cnf?

I have never even looked at this file before.

> **Joe of loath said:**
> It sounds like your PC is only connecting to the network when logged in, which is how network manager works.

The simplest way is to setup wicd, which runs at boot whether you log in or not.

I should mention, the computer is running a site w/ Apache.  The website is accessible even when I am unable to SSH to the computer.

---

### Post by hawkmage on 2011-02-15
The only reason I mentioned it is that I had an issue with sshd starting after upgrading to 10.10 because I had changed my openssl.cnf to use $HOME to define default locations for openssl and when booting this variable did not exist preventing sshd from starting.

What do you have in /etc/init/ssh.conf in the line "start on"

---

### Post by Gakumerasara on 2011-02-15
> **hawkmage said:**
> What do you have in /etc/init/ssh.conf in the line "start on"
start on filesystem

---

### Post by hawkmage on 2011-02-16
That is the normal "start on" for ssh.  This should make sshd start when the mountall.conf runs.  

This is odd, do you have anything in the fstab that mounts when you login?

---

### Post by Gakumerasara on 2011-02-16
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=611e45e5-0e95-49a0-9ef4-fac81dc74c2e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e800704d-916f-4368-9cfe-88cb10f876ac none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0



There is a 4GB USB drive that mounts when I login, but it's not listed in fstab.

---

### Post by hawkmage on 2011-02-16
Noting odd there.  I have no idea where to go from here.

---

