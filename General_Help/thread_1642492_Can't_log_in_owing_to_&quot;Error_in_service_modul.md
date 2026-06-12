---
title: "Can't log in owing to &quot;Error in service module&quot;"
date: 2010-12-10
forum: General Help
---

### Post by cossins71 on 2010-12-10
Hi,
  I have an acer aspire one 150A running Ubuntu 10.04 netbook remix. Some weeks ago the netbook would not boot up and after fiddling for a while It came back to life but I was unable to login with the message "unable to open session". If I tried to log in from the terminal it told me "error in service module"

Their is already a post about this issue which I have added to, [http://ubuntuforums.org/showthread.php?t=1523153](http://ubuntuforums.org/showthread.php?t=1523153) . However, no one has posted a solution so I thought I would create a new thread to see if anyone would reply.  Apologies if this is not the correct procedure as I have only just joined this forum in an attempt to sort this issue out.

Many thanks

Ben

---

### Post by TeoBigusGeekus on 2010-12-10
A quick googling of the error message gave [this]("http://www.linuxforums.org/forum/suse-linux/63144-error-service-module.html").
Mind you, it is a bit old, but you have nothing to lose.

---

### Post by cossins71 on 2010-12-11
Hi,
  Thanks for your reply. Yes I saw this thread too and the information about this pam file, I have seen similar things on other threads. However, as it says in that thread you still have to login to get access to the pam file. Some on that thead managed this through some form of remote login. Unfortunately I am not in a possition to be able to do this as I am on holiday in South America and only have a single laptop.
  I did see another thread suggesting a way in through the grub menu. For some reason though I cannot get the grub menu to stay up, it instantly reverts to the boot screen as I only have one os installation. I think this may be an issue with Grub2 or something.

Thanks

Ben

---

### Post by cossins71 on 2010-12-26
Hello all,
  I have now managed to get access to my laptop through the live cd. However the pam.d/login file is different from those cited on other web forums and I am not sure which lines I should be commenting? Is there anyone who can help me with this. I guess Ubuntu is different from the suse explainations I have seen.

Thanks in advance
Ben

---

### Post by dave373 on 2011-01-28
I too have this problem.

I have been putting off fixing it for a couple of months now.

Have you had any luck fixing it?

---

### Post by dave373 on 2011-01-28
Yay.. I got mine fixed..

I had a corrupted filesystem which had killed the /lib/security/pam_limits.so file.

Firstly, I forced a filesystem check 

```
touch /forcefsck
```

I copied the file from a working machine and I can now login.

I still have some issues with the keyrings, but these are minor problems.

Hope this helps someone :)

---

