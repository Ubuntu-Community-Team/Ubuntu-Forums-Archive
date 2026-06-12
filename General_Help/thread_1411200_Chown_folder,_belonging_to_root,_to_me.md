---
title: "Chown folder, belonging to root, to me"
date: 2010-02-19
forum: General Help
---

### Post by DeMus on 2010-02-19
Hi,

I have just re-installed Jaunty 64. I have an external hard-disk which I use for back-up and to store movies. This disk is separated into 2 partitions:
1. ext4, which is formatted as ext4
2. NTFS, which is formatted as NTFS

After re-connecting the disk, the ext4 partition belongs to me, the NTFS partition belongs to root.
I want to share a folder in the NTFS partition but since root owns it I can not do that. So, I tried to chown the folder, which resides in /media, so I am the owner. But it doesn't work. I tried it as user, I tried it as root.
What to do?

---

### Post by Cilionelle on 2010-02-19
I have a similar problem with an ext3 partition.  Eagerly awaiting an answer...

---

### Post by doas777 on 2010-02-19
well, i did a little looking arround, because ntfs ownership is not like extx ownership.
make sure you are using the ntfs-3g driver to mount your ntfs partition, and if you have problems you may need to install ntfs-config

but those were some old threads so be careful.
```
sudo apt-get install ntfs-config 
```

---

### Post by doas777 on 2010-02-19
> **Cilionelle said:**
> I have a similar problem with an ext3 partition.  Eagerly awaiting an answer...


for ext3, you should be able to just use chown.
```

sudo chown -R newowner:newownergroup pathtodir

```

---

### Post by Cilionelle on 2010-02-19
> **doas777 said:**
> for ext3, you should be able to just use chown.
```

sudo chown -R newowner:newownergroup pathtodir

```
What would "newowner:newownergroup" look like in reality?  My user name is tom and I'm not part of any groups...
Oh, and is the "pathtodir" the /dev/sda2 or the /media/extra?

PS: Thanks!

---

### Post by San_SS! on 2010-02-19
Hi!

You should first mount the partition. For example in /media/extra/

When you add a user it automatically creates a group with the same name as your username. So:

```

$sudo chown -R tom:tom /media/extra

```

I hope you find this information useful.

---

### Post by doas777 on 2010-02-19
> **Cilionelle said:**
> What would "newowner:newownergroup" look like in reality?  My user name is tom and I'm not part of any groups...
Oh, and is the "pathtodir" the /dev/sda2 or the /media/extra?

PS: Thanks!


ok, lets say my username is bob. by default files i create will be owned by "bob:bob" (a users default group is a group of one; themselves). 

the path, shoudl be the path to the mounted location not the device itself. so if I wanted to alter somthing mounted to /media/disk2 I would use this full command:

```

sudo chown -R bob:bob /media/disk2

```

becareful with the '-R' though. it tells chown to repeat the action on all subdirectories and files.

now on groups; I share files with samba that I want accessible to multiple user accounts. i created a group called sambapeople, and added the users to that group. for those locations I would want to use chown like this:
```
sudo chown -R bob:sambapeople /media/disk2
```
but in order to do that, /media/disk2 needs to have permissions that allow the group to perform the desired function. just being a member of the owner group does not automatically apply group permissions to an object.

---

### Post by rnerwein on 2010-02-19
hi
you are for sure member in groups. on command line just type: [COLOR=DarkOrange]id -a[/COLOR]  this will show you your username - you said tom and all the groups you are of. the first group after your username ( if you are the administrator is the same group name as your username i guess) is your primary group.
about the permission of the ntfs filesystem - here is  my fstab entry which works for me (vista_data is a directory i have created at / )

/dev/sda3 /vista_data ntfs defaults,noauto,umask=000    0 0

if you want to have the file system  mounted at boot time, change [COLOR=Red]noauto[/COLOR] to [COLOR=Lime]auto[/COLOR] .

to edit /etc/fstab you must be root ( sudo )

ciao

---

### Post by DeMus on 2010-02-19
Even with all the help you give me, I still can not change the ownership of the movies folder on my NTFS formatted partition.
I have installed the ntfs-3g driver, the partition is mounted automatically when the drive is connected.
What else do I need to do?

---

