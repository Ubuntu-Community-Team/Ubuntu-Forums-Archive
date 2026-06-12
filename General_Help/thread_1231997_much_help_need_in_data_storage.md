---
title: "much help need in data storage???"
date: 2009-08-05
forum: General Help
---

### Post by tdmeskimo on 2009-08-05
i tried some things on my own and i am not getting success.  I have two desktops each with sda with swap, /; and sdb /home and a laptop with a singe drive.  the desktop i fig by 9.04 in the live cd to set up the desktops with 2 hdd.  this is a compunded proble call for help.  i need to learn how to mount a 3 hdd on to one desktop and sata drive that is removeable but not hotswapable it is just an external drive holder on the front of my desktop.  i need to learn how to format, mount on boot up so when the backup runs it will backup to the sdc as /backupsystem.  then also i like to backup the 2nd desktop over the network to the /backupsystem and my laptop to /backupsystem over the network.  help help help me please i have search how to format got that with partition editor for gnome but how do you automaticaly mount on boot up and it will not let me write to?!? something about permition and location?!?!?!? help help please i am at a loss? so looking for help on the 3rd hdd and backup software that will allow to backup the /home data from all three systems to a single drive on one of my desktops as /backupsystem thanks in advance

---

### Post by soapBAR2 on 2009-08-05
Firstly, I assume you've got the disk formatted with gparted, and let's assume you used ext3. Secondly, you'll want to make a directory to mount the disk in.

```
sudo mkdir /mnt/yourmountpoint
```

It's considered good form to mount drives in the /mnt/ folder, but you don't have to. Next, what you want to do is backup fstab:

```
sudo cp /etc/fstab /etc/fstab.backup
```

Then, you want to edit /etc/fstab

```
sudo nano /etc/fstab
```

(Be *EXTREMELY* careful with this file, and make sure you have a livecd handy).

The format is 
<file system> <mount point> <type> <options> <dump> <pass>

So,
/dev/yourpartitionnamehere /mnt/yourmountpoint ext3 relatime,errors=remount-ro 0 0

where /dev/yourpartitionnamehere is your partition name (if you have files like /dev/sda and /dev/sda1, you want the one with the longer name). Don't worry about dump or pass, just set them both to zero.

```
man fstab
```

For more details. Then, if you've got it all properly edited, drop back into terminal (in nano, CTRL+x, y, enter) and type

```
sudo mount -a
```

This will mount everything in your /etc/fstab. Your machine SHOULD auto-mount /etc/fstab on startup, but sometimes it doesn't, so just add a script to run sudo mount -a or manually do it on ever startup.

For backup, you can use rsync or samba, your choice. I think samba is easier (best option is to just mount it with filesystem=cifs and options user=yourusename,pass=yourpass,noperm), but rsync is designed for backup and is extremely elegant and efficient. Google for tutorials on how to set either of these up.

---

### Post by tdmeskimo on 2009-08-06
soapBAR2 "Firstly, I assume you've got the disk formatted with gparted, and let's assume you used ext3. Secondly, you'll want to make a directory to mount the disk in."


yes i formatted with gparted, but i used ext4, so will the rest matter or should everything still work?

some how i lost the quates so i put them in, and thanks for the reply.

---

### Post by tdmeskimo on 2009-08-08
> **soapBAR2 said:**
> Firstly, I assume you've got the disk formatted with gparted, and let's assume you used ext3. Secondly, you'll want to make a directory to mount the disk in.

```
sudo mkdir /mnt/yourmountpoint
```

It's considered good form to mount drives in the /mnt/ folder, but you don't have to. Next, what you want to do is backup fstab:

```
sudo cp /etc/fstab /etc/fstab.backup
```

Then, you want to edit /etc/fstab

```
sudo nano /etc/fstab
```

(Be *EXTREMELY* careful with this file, and make sure you have a livecd handy).

The format is 
<file system> <mount point> <type> <options> <dump> <pass>

So,
/dev/yourpartitionnamehere /mnt/yourmountpoint ext3 relatime,errors=remount-ro 0 0

where /dev/yourpartitionnamehere is your partition name (if you have files like /dev/sda and /dev/sda1, you want the one with the longer name). Don't worry about dump or pass, just set them both to zero.

```
man fstab
```

For more details. Then, if you've got it all properly edited, drop back into terminal (in nano, CTRL+x, y, enter) and type

```
sudo mount -a
```

This will mount everything in your /etc/fstab. Your machine SHOULD auto-mount /etc/fstab on startup, but sometimes it doesn't, so just add a script to run sudo mount -a or manually do it on ever startup.

For backup, you can use rsync or samba, your choice. I think samba is easier (best option is to just mount it with filesystem=cifs and options user=yourusename,pass=yourpass,noperm), but rsync is designed for backup and is extremely elegant and efficient. Google for tutorials on how to set either of these up.


i am closing this thread
thanks for your help everything worked fine, the only diffrence is that i used the uuid in the editing of the fstab, and now my 500gb sata drive is mounted as /backup in my /, thanks man

as far as backup i found back in time reviewed by category5.tv found in to be what i need.

---

