---
title: "FSCK Message:  fsck from util-linux-ng 2.17.2"
date: 2011-05-01
forum: General Help
---

### Post by cat2005 on 2011-05-01
Has anyone received the following FSCK message: 

fsck from util-linux-ng 2.17.2

I am testing Ubuntu 10.10 32-bit in Virtual Box.  After doing some program downloads, user account setups, etc, I had an "error" message appear during reboot.

To learn more, I went to terminal and input:  fsck -N

and got this:

fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)

I tried fixing this, both automatically (gparted fsck and manual fsck) but the item still appears when I go into terminal and type:  fsck -N

Google searches show others who have received this have had boot up problems.  I don't appear (so far) to have such problems, but nothing I do gets rid of the "fsck from util-linux-ng 2.17.2" notice in terminal.

What is this?  Is it going to cause trouble in the future?

Thanks.

---

### Post by cat2005 on 2011-05-07
Bump.  Anyone?  Bueller?

---

### Post by matt_symes on 2011-05-07
Hi

> **cat2005 said:**
> Has anyone received the following FSCK message: 

fsck from util-linux-ng 2.17.2

I am testing Ubuntu 10.10 32-bit in Virtual Box.  After doing some program downloads, user account setups, etc, I had an "error" message appear during reboot.


What was the exact error message ?

> 
To learn more, I went to terminal and input:  fsck -N

and got this:

fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)

I tried fixing this, both automatically (gparted fsck and manual fsck) but the item still appears when I go into terminal and type:  fsck -N

Google searches show others who have received this have had boot up problems.  I don't appear (so far) to have such problems, but nothing I do gets rid of the "fsck from util-linux-ng 2.17.2" notice in terminal.

What is this?  Is it going to cause trouble in the future?

Thanks.

What was the exact fsck command you entered ?

fsck -N my my machine gives

```
matthew@matthew-laptop:~$ fsck -N
fsck from util-linux-ng 2.17.2
[/sbin/fsck.ext4 (1) -- /] fsck.ext4 /dev/sda5 
[/sbin/fsck.ext4 (1) -- /home/matthew/my_documents] fsck.ext4 /dev/sda8 
[/sbin/fsck.ext4 (1) -- /home/matthew/storage] fsck.ext4 /dev/sda16 
[/sbin/fsck.ext4 (1) -- /home] fsck.ext4 /dev/sda7 
matthew@matthew-laptop:~$ 
```

This is basically telling me what partitions it would check if i ran fsck and the commands it would run. It will not check any of the partitions until i tell it what partitions to check.

Your post is unclear. What exactly have you run ? What exactly have you tried ?

As you don't want to run fsck on a mounted drive, your best best might be to type (from a terminal)

```
sudo touch /forcefsck
```

BTW: I don't use Ubuntu in a VM. I might need to set one up to help you. I am unsure how fsck operates under a VM.

Kind regards

---

### Post by cat2005 on 2011-05-16
matt_symes

Sorry it has taken me so long to reply.  I haven't been able to get online lately.

I entered the following in termina (I tried it with sudo too)l:

 fsck -N

I got this output:

fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)

I haven't tried it since then.

Unfortunately, I can't remember if I tried it on a mounted disk or not.  

Could I try to run the command via Ubuntu LiveCD?

Thank you.

---

### Post by matt_symes on 2011-05-20
Hi

> **cat2005 said:**
> matt_symes

Sorry it has taken me so long to reply.  I haven't been able to get online lately.

I entered the following in termina (I tried it with sudo too)l:

 fsck -N

I got this output:

fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)

I haven't tried it since then.

Unfortunately, I can't remember if I tried it on a mounted disk or not.  

Could I try to run the command via Ubuntu LiveCD?

Thank you.

If you want to run fsck on the VM image file, boot into the VM image then open a terminal and type

```
sudo touch /forcefsck
```Then reboot your VM machine and it should run fsck for  you. Try this. Does it run fsck ?

```
fsck -N
```will tell you what fsck will do, but it will not do it. In a VM with 9.10 running i get

```
matthew@matthew-laptop:~$ fsck -N
fsck from util-linux-ng 2.16
[/sbin/fsck.ext4 (1) -- /] fsck.ext4 /dev/sda1 
matthew@matthew-laptop:~$ 
```This is telling me it will run fsck.ext4 on device /dev/sda1 on /.

I would expect you to get similar output when running the command.

Kind regards

---

