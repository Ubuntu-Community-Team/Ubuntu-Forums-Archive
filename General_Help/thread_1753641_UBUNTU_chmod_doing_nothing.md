---
title: "UBUNTU chmod doing nothing"
date: 2011-05-09
forum: General Help
---

### Post by luisridaocruz on 2011-05-09
I have installed UBUNTU 11.04 on my machine.
I'm trying to build a program from source but cannot change
the permissions to execute it.

LRC $ ./configure BUILD_64BIT=yes
bash: ./configure: Permission denied

LRC $ chmod 777 configure

LRC $ ls -l
total 173
-rw------- 1 luisridaocruz luisridaocruz 145899 2011-04-08 22:30 configure
drwx------ 1 luisridaocruz luisridaocruz   4096 2011-04-08 22:30 docs
drwx------ 1 luisridaocruz luisridaocruz      0 2011-04-08 22:30 examples
.....
.....

It does not work with any files no matter the directory or file I choose.
What is going on?

Best

---

### Post by Dave_L on 2011-05-09
What are the permissions of the directory containing those three items?

---

### Post by DanneStrat on 2011-05-09
> **luisridaocruz said:**
> I have installed UBUNTU 11.04 on my machine.
I'm trying to build a program from source but cannot change
the permissions to execute it.

LRC $ ./configure BUILD_64BIT=yes
bash: ./configure: Permission denied

LRC $ chmod 777 configure

LRC $ ls -l
total 173
-rw------- 1 luisridaocruz luisridaocruz 145899 2011-04-08 22:30 configure
drwx------ 1 luisridaocruz luisridaocruz   4096 2011-04-08 22:30 docs
drwx------ 1 luisridaocruz luisridaocruz      0 2011-04-08 22:30 examples
.....
.....

It does not work with any files no matter the directory or file I choose.
What is going on?

Best

Hello.

Have you tried giving yourself permissions to the "LRC" folder you're in?

Try to "chmod 777" on it too and see if it fixes your problem.

---

### Post by luisridaocruz on 2011-05-09
LRC $ chmod 777 /media/Data/ADMB/admb-10.1
LRC $ ls -l
total 173
-rw------- 1 luisridaocruz luisridaocruz 145899 2011-04-08 22:30 configure
drwx------ 1 luisridaocruz luisridaocruz   4096 2011-04-08 22:30 docs
drwx------ 1 luisridaocruz luisridaocruz      0 2011-04-08 22:30 examples
-rw------- 1 luisridaocruz luisridaocruz   1673 2011-04-09 06:27 LICENSE
-rw------- 1 luisridaocruz luisridaocruz    767 2011-04-09 06:27 Makefile
-rw------- 1 luisridaocruz luisridaocruz   6774 2011-04-09 07:55 README.txt
drwx------ 1 luisridaocruz luisridaocruz   4096 2011-04-08 22:29 scripts
drwx------ 1 luisridaocruz luisridaocruz   4096 2011-04-08 22:30 src
-rw------- 1 luisridaocruz luisridaocruz      5 2011-04-09 06:27 VERSION

Nothing happens

Best

---

### Post by ~Plue on 2011-05-09
Are the files on a NTFS partition? If that is the case, you cant set linux filesystem permission on those files.

You'll need to either mount the partition with the exec flag or move those files to your home folder and then change the permissions.

---

### Post by ksprasad on 2011-05-09
Hi,
 
Try adding sudo.
 
$sudo chmod 777 configure

Regards,
ksprasad

---

### Post by luisridaocruz on 2011-05-09
It didn't work with sudo chmod 
but following ~Plue advise I tried
to move to my home folder

And now it's working.

Thanks a lot
Best,
luis

---

