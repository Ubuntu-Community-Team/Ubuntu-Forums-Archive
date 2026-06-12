---
title: "Cron job as root, priveleged access"
date: 2010-09-22
forum: General Help
---

### Post by Butcher0 on 2010-09-22
Hi!

I have two users in my system. Admin(Root) , and "student". I am making a bootable USB with Ubuntu 10.04 with two partitions. 

What i need is a cron-job who copies some files that the student has made(from the first partition) onto a partition which he is not allowed to access. The way i thought it should be done was making a root cron-job which mounts the drive and then copies the documents, and maybe unmounts it again. 

The problem with this is that, when i mount it, wouldnt it be accessible to the "student" as well then? Since i give him sudo-rights and mounts the drive in the background for him? Alternatively i could unount it straight after the copying is done, but then it would do this too often I guess.

Any thoughts/solutions on this is highly appreciated. 

Thanks in advance!

---

### Post by lloyd_b on 2010-09-22
> **Butcher0 said:**
> Hi!

I have two users in my system. Admin(Root) , and "student". I am making a bootable USB with Ubuntu 10.04 with two partitions. 

What i need is a cron-job who copies some files that the student has made(from the first partition) onto a partition which he is not allowed to access. The way i thought it should be done was making a root cron-job which mounts the drive and then copies the documents, and maybe unmounts it again. 

The problem with this is that, when i mount it, wouldnt it be accessible to the "student" as well then? Since i give him sudo-rights and mounts the drive in the background for him? Alternatively i could unount it straight after the copying is done, but then it would do this too often I guess.

Any thoughts/solutions on this is highly appreciated. 

Thanks in advance!
First, you can set the permissions when mounting a filesystem.  Which means you can easily make that second partition only accessible to root.

Second, if you give "student" full access to "sudo", then he has full access to everything in the system, which I gather you don't want.

Could you describe in a bit more detail what you're trying to do?  There are a number of options, but which one is best depends on your needs.

At first glance, what I *think* you want is:
1.  Set the permissions on the second partition so that it's only accessible by root. 
2.  Have a root-owned cron job that periodically copies files from somewhere in the system to that partition.

With this setup, you can mount that partition at boot time, and leave it mounted, and "student" won't be able to see or touch any of the files on it.

Lloyd B.

---

### Post by Butcher0 on 2010-09-24
Thanks Lloyd! That`s exactly what I was hoping to achieve. Think I have it solved now.

Appreciated your help.

---

