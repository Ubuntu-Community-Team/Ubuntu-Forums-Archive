---
title: "Only some folders openable on ext4 partition"
date: 2011-12-10
forum: General Help
---

### Post by rng on 2011-12-10
I created an ext4 partiion on free space of my hard disk using gparted for storing some data. I copied some folders to it from other partitions. Now I have permission to  access only some partition but for others I have to use command 'sudo nautilus'. Why has this happened and can I change it so that I can access all folders without using sudo?

Thanks for your help.

---

### Post by lukeiamyourfather on 2011-12-10
Yes, use chown to change the owner. It will require sudo since it thinks you don't already own them. For example a command is below.

```

cd /mnt/yourNewHardDisk
sudo chown yourUser:yourGroup *

```

---

### Post by rng on 2011-12-10
Thanks. I know my username (can also confirm it by command 'whoami') but I do not know my group name. How can I find it?

---

### Post by lolpenguin on 2011-12-10
If you require root access on graphical applications "gksu program" works better, and you can do it using alt+f2. You have to install gksu if you don't have it.

---

### Post by killermist on 2011-12-10
You probably have a group (same as your username) that is just you too.

In my case, I use 
```
chown -Rc killermist:killermist /media/somedrive
```
(-R is recursive, -c is "show changes only", they combine as -Rc)
It might also be a good idea to follow it up with 
```
chmod u+rwX /media/somedrive
```
which will set for the _u_ser _r_ead and _w_rite permissions and e_X_ecutable on directories (to enable listableness if they didn't have it already) and files already executable

---

### Post by rng on 2011-12-11
Thanks for the info. 

Currently, I am getting my work done as follows: I open a console and give command 'sudo nautilus' . From this nautilus window I am able to open any file and work on any document on this partition. My question is whether it is safe to work like this all the time or better to change the permissions of the partition with chown and chmod commands?

---

### Post by coffeecat on 2011-12-11
> **rng said:**
> My question is whether it is safe to work like this all the time or better to change the permissions of the partition with chown and chmod commands?

My preference would be to chown and chmod what I need on the partition and be done with it. A gksu nautilus browser is a loaded gun.

Either do a recursive chown and chmod on everything, or do selective chowns and chmods on different folders, depending on your needs.

One useful trick. If you don't know your default group (which is usually the same name as your user account, as someone has already mentioned) you can:

```
sudo chown yourusername: /path/to/files
```

Note the trailing colon after your username. The system fills in the default group for you. That works with chmod as well.

---

### Post by dFlyer on 2011-12-11
> **rng said:**
> Thanks. I know my username (can also confirm it by command 'whoami') but I do not know my group name. How can I find it?

Your user name and group name should be the same if your the administrator of your system as such:

sudo chown yourname:yourname filename or directory.

If you want to change all files so your the owner of a directory use:

sudo chown -R yourname:yourname /directory

---

### Post by rng on 2011-12-11
The partition has about 45 gb data (most are inaccessible without sudo). Will the chown command list all the files? It will take a long time.

---

### Post by lukeiamyourfather on 2011-12-12
> **rng said:**
> The partition has about 45 gb data (most are inaccessible without sudo). Will the chown command list all the files? It will take a long time.

If you change the owner of a directory it will change everything in that directory as well. It might take a little while, like five or ten minutes to apply to everything on the disk (maybe more depending on how many files there are). To answer an earlier post, working as root (e.g. with sudo) all the time is **_not_** safe. The use of root (and sudo) should be limited to administrative tasks only.

---

### Post by rng on 2011-12-12
I issued chown command as suggested and it went off without a hitch. The partition is accessible now and the script files are executable (I did not need to issue chmod command). 

Thanks everyone for your help.

---

### Post by rng on 2011-12-12
Will the permissions get disturbed if I now change the label of the partition?

---

### Post by coffeecat on 2011-12-13
> **rng said:**
> Will the permissions get disturbed if I now change the label of the partition?

No. That should make no difference.

---

### Post by rng on 2011-12-13
Thanks.

---

