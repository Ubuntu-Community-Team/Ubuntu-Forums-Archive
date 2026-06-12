---
title: "fstab problems"
date: 2012-01-07
forum: General Help
---

### Post by MadJestyr on 2012-01-07
Having some issues with some new fstab entry's I am trying.  I installed VirtualBox to run a VM of Windows 7 for netflix and Starcraft II.  I reformatted my old windows partition so that I could store the VM's there.  Trying to fstab the copied /VirtualBox VMs folder from my mounted partition over the folder /home/madjestyr/VirtualBox VMs.  The Storage scheme I created some years ago works like a charm, but I can't get the new VM scheme entries to work properly.  I am not sure what I am missing.

## Storage scheme
/dev/sda5	/media/storage	ext2	defaults,user,nosuid,nodev	0	0
/media/storage/fstab/Videos	/home/madjestyr/Videos	none	bind
/media/storage/fstab/Pictures	/home/madjestyr/Pictures	none	bind
/media/storage/fstab/Music	/home/madjestyr/Music	none	bind
/media/storage/fstab/Backup	/home/madjestyr/Backup	none	bind
/media/storage/fstab/Documents	/home/madjestyr/Documents	none	bind
/media/storage/fstab/Photos	/home/madjestyr/Photos	none	bind


## VM scheme
/dev/sda3	/media/vm	ext2	defaults,user,nosuid,nodev	0	0
/media/vm/VirtualBox\ VMs	/home/madjestyr/VirtualBox\ VMs	none	bind

sudo mount -a 
[mntent]: line 28 in /etc/fstab is bad

Line 28 is:  /media/vm/VirtualBox\ VMs	/home/madjestyr/VirtualBox\ VMs	none	bind

boot.log reads
mount: unknown filesystem type '/home/madjestyr/VirtualBox'
mountall: mount VMs [977] terminated with status 32
mountall: Filesystem could not be mounted: VMs
Skipping VMs at user request

and it is creating a VMs folder in root whenever I boot.  The partition sda3 mount just fine.  It is the folder VirtualBox VMs that won't mount properly.  I am sure it is the space but I don't know of any other way of dealing with that other than the backslash.

Not sure what I missed or how I need to re-write that line but it is very frustrating.

---

### Post by 2F4U on 2012-01-07
I was tempted to answer "don't use a space character in you path names". Hope the following helps

[http://www.webmasterworld.com/forum40/674.htm](http://www.webmasterworld.com/forum40/674.htm)

---

### Post by dino99 on 2012-01-07
[Tab] is usefull to get the path without error: enter the /media/ then press Tab, and so on

---

### Post by satanselbow on 2012-01-07
> **2F4U said:**
> I was tempted to answer "don't use a space character in you path names". Hope the following helps

[http://www.webmasterworld.com/forum40/674.htm](http://www.webmasterworld.com/forum40/674.htm)

Spaces can be overcome with **\040**

ie:

```

//servername/my\040documents   /mnt/MyDocs   cifs   username=username,password=password,uid=1000,_netdev,rw,nofail   0 0

```

---

### Post by MadJestyr on 2012-01-07
> **satanselbow said:**
> Spaces can be overcome with **\040**

ie:

```

//servername/my\040documents   /mnt/MyDocs   cifs   username=username,password=password,uid=1000,_netdev,rw,nofail   0 0

```

Thanks.  That solved my problem.

---

### Post by MadJestyr on 2012-01-07
> **2F4U said:**
> I was tempted to answer "don't use a space character in you path names". Hope the following helps

[http://www.webmasterworld.com/forum40/674.htm](http://www.webmasterworld.com/forum40/674.htm)

thanks

---

### Post by MadJestyr on 2012-01-07
> **dino99 said:**
> [Tab] is usefull to get the path without error: enter the /media/ then press Tab, and so on

There are tabs, it just doesn't show that when I copy/pasted.  I usually just read forums.  Not post to them.  :)

---

