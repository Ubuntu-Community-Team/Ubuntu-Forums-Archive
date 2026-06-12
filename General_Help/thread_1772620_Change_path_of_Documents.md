---
title: "Change path of Documents"
date: 2011-05-31
forum: General Help
---

### Post by johnm99 on 2011-05-31
I have a dual boot Win 7 and Ubuntu 11.04 I just started setting up - and know almost nothing about Linux - I have all my data on separate drives from my OS drives, and would like to "arrive" at my "My Documents" file when i choose "Documents" in Ubuntu. 

The location of "My Documents" is  -** /media/New Volume/My Documents**  (which I found by dragging the folder onto the terminal)

not quite sure how to put in the right command - something like 

**ln -s /media/New Volume/My Documents ~Documents** - (but that isn't right and didn't work).

I also want to do the same with Music, Pictures and Videos.

Anyone know how to do this?
Many thanks
John

---

### Post by ruffEdgz on 2011-05-31
The command looks like it can work but just needed to add a '/' after the '~':
```

sudo ln -s /media/New\ Volume/My\ Documents ~/Documents

```
Just change the 'Documents' to whatever other directory you want to symbolically link to your Ubuntu Home Directory.

---

### Post by oldfred on 2011-05-31
I learned a while back to stop using spaces. Use CamelCase or under_score or just onebiglongname. Windows will work without the spaces and it makes things a lot simpler in Linux.

If you have one partition with many folders.
#Or link all with one command:
for i in `echo /mnt/data/*`;do ln -s $i; done

Are you mounting your shared NTFS partition with fstab? So it is always mounted when you boot?

NOTE: The mount point can be anywhere. If it's in your /home or /media folders it will show up under "Places". If it's directly off "/" or /mnt it will not.

sudo mkdir /mnt/data
sudo chown -R fred:fred /mnt/data
sudo chmod -R 766 /mnt/data
#Edit fstab with your UUID:
UUID=a55e6335-616f-4b10-9923-e963559f2b05  /mnt/data ntfs-3g defaults                0  2 
#Verify entry is ok, if no errors it is:
sudo mount -a
#from home so default location of link is in /home/fred
mv Music oldMusic
# Music is a folder in the partition mounted as /mnt/data
ln -s /mnt/data/Music
#Or link all folders with one command:
for i in `echo /mnt/data/*`;do ln -s $i; done

Shared NTFS partition:
[http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

---

### Post by ruffEdgz on 2011-05-31
> **oldfred said:**
> 
for i in `echo /mnt/data/*`;do ln -s $i; done
 +1 for this command. I do love an easy one-liner like this one ;)

---

