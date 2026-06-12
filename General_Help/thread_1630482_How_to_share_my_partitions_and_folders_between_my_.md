---
title: "How to share my partitions and folders between my ubuntu &amp; network windows pcs"
date: 2010-11-25
forum: General Help
---

### Post by s.shawky on 2010-11-25
please help
i want the best way to share my folders between my Ubuntu computer and other windows computers through the local network

---

### Post by rusty149 on 2010-11-25
```
sudo apt-get install system-config-samba
```
 
This will install a good gui program to configure shares. Open it from System>Administration.

---

### Post by apollothethird on 2010-11-25
> **s.shawky said:**
> please help
i want the best way to share my folders between my Ubuntu computer and other windows computers through the local network

For Linux you can use NFS.

[indent]Make sure you have NFS installed on your computer:

apt-get install nfs-common (Install this on both the server and client.)

Create/edit an /etc/exports file:
```
sudo gedit /etc/exports
```

Please in the exports file a directory that you’ll be sharing (exporting) to the network. The format is:
```
 # Directory-to-export          Computer-given-permission
/home client-computer(rw,async,no_root_squash,subtree_check)
```

You separate the computers given permission each with an entry separated by a space.

Active the new configuration with:

```
exportfs –av
```

Now for the client computer you want to connect to this share you use the command:

```
sudo mount host-computer:/shared-directory /mnt/mountname
```

You now have that shared space available in /mnt/mountname[/indent]



You can also use Samba (which Windows have default drivers for):

[indent]Make sure you have samba installed on your computer:

sudo apt-get install samba-common (Install this on both the server and client.)

You can share the space by right clicking on the folder in nautilus and following the prompts.  You can link to the share from other Linux computers with the commandline:

```
sudo mount -o username=userid host-computer:/shared-directory /mnt/mountname 
```[/indent]

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by s.shawky on 2010-11-25
> **rusty149 said:**
> ```
sudo apt-get install system-config-samba
```
 
This will install a good gui program to configure shares. Open it from System>Administration.

this message appears when i try to open samba 
[IMG]http://sphotos.ak.fbcdn.net/hphotos-ak-snc4/hs1124.snc4/148655_1706662907600_1268877256_1925035_7016371_n.jpg[/IMG]

---

