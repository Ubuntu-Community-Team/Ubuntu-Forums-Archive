---
title: "Adding an additional hard drive (I'm Stuck)"
date: 2009-12-12
forum: General Help
---

### Post by Whodoes on 2009-12-12
I have Ubuntu 8.1 (a fresh install) on an older machine. Ive added Boxee and have just installed a 160gbIDE drive formatted (via Gparted). It is now Fat32. The partition manager displays the following

Filesystem:fat32
blah blah...
Path   :/dev/sdb1
Status : not mounted
label  : BoxeeShare

--------------
My intention is for this drive to be shared and usable on my windows network so that my folks can drag media (from their windows machines) to this drive for display via the Boxee front end running on this linux box.

What information i've found is limited to copy/paste terminal instructions which i dont understand...

thoughts ?

---

### Post by lmarmisa on 2009-12-12
I would like to make a couple of comments:

1) You have selected FAT32 for your new 160 Gbytes drive. I think that ext3 would be better. FAT32 is an old format oriented to Windows systems. I would change to ext3.

2) You have to mount this new drive. I suppose that you have reformated your /dev/sdb1 partition with ext3 file system. 

Open a terminal and type:

```

sudo bash
mkdir /media/multimedia
gedit /etc/fstab

```Append this two lines:

```

...
# /media/multimedia on /dev/sdb1
/dev/sdb1 /media/multimedia ext3 errors=remount-ro 0 1

```Save the file and restart your system.

Now the new hard disk is mounted in /media/multimedia . Configure Boxee for this directory.

I would like this information to be useful for you.

Best regards,

Luis

---

### Post by OpSecShellshock on 2009-12-12
Wouldn't formatting it as ext3 cause interoperability issues with the users being able to write their files to it from Windows?

---

### Post by lmarmisa on 2009-12-12
I suppose that Windows users are located in other computers and your older computer runs only Ubuntu. Is it right?.

In this case, ext3 is the right choice.

The ext3 file system is only internal to your machine. Use samba and Boxee for sharing your files.

Regards,

Luis

---

### Post by Whodoes on 2009-12-12
i chose FAT32 because, as i understand it, if i want a windows machine to be able to read/write to the drive ext3 wont work. If thats not correct i'll remortmat it since there isnt anything on it yet. 

as an aside, isnt there some way of mounting a drive without needing to copy/paste all sorts of code into terminal which i dont understand ? 
 im new to linux but it seems that every time ive tried to get a systme up and running i end up needing to run long strings of opaque terminal commands. is there something with a GUI out there ?

---

### Post by ST3ALTHPSYCH0 on 2009-12-12
The reason that EXT3 is the right choice is because your OS (Ubuntu ) is serving the files to the other machines.... they don't actually read the partition. 
In order for this to happen you'll need to auto-mount the drive on start up (that's the reason for editing the fstab file). Psydm is a GUI to do this, you can either search for it in synaptic or paste this command in the terminal:
```

sudo apt-get install pysdm

```
 You'll also need Samba for file sharing with windows machines. Search for samba in synaptic (I d/led Samba4) also there's a graphic frontend for samba configuration that'll be listed when you search for samba. I recommend you install it too.

---

