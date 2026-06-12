---
title: "NFS Sharing - Local Network"
date: 2012-08-30
forum: General Help
---

### Post by Quarkrad on 2012-08-30
I'm loosing the will to live trying to get my head round this 'quote' simple thing to set up on Ubuntu.  I would like to delete everything and start again but that also is no easy to find out how to do. I need help with some simple documentation rather than the classic Ubuntu docs that jump from level 1 to 100 on the same page.

I have two 12.04 machines in the same room connected via an ethernet lan.  I don't want any passwords - just simple read/write access for both users on each others machine (or rather to specific folders).  I have a slight complication in that although we do not use Windows we do each have folders on NTFS partitions that we would aslo like to share with each other. However, before that, I'm trying to access each others Documents folders on our ext4 Ubuntu partitions.  Sometimes the other users machine appears in Places/Browse Network but sometimes not(?).  Sometimes I get asked for a password and sometimes not(?).  Docs that go down the terminal route seem to be aimed at wans rather than lans - I don't believe I need SSH for my wife and self, two machines 6 inches apart.  I'm trying to use the gui way but when I need to choose the samba user the window is empty - I have no users.  I did see myself once but the list was the same as when changing folder permissions on my machine - I was trying to select my wife as the user as it is she who I'm trying to share with.  I'm at the stage where I'm not seeing the wood for the trees - trying to go back to square one for my simple set up.  Is samba the best way to share/read/write/create files/folders on each others machines?

---

### Post by LewisTM on 2012-08-30
Since you are sharing between Linux machines only, on a local network, I would strongly advise you go with NFS instead of Samba. It's fast, transparent, stable and surprisingly easy to setup.

Here's a strategy that might work well in your case. I assume that you (Quarkrad) and your wife (I'll call her Sandra) have the same UID (1000) on your respective machines. If not, I'll need to make modifications. The numerical user ID can be found with the [FONT="Courier New"]id[/FONT] command. I also assume that Quarkrad is not a user in Sandra's Ubuntu box and vice versa.

1. Install the nfs server package on both machines
```
sudo apt-get install nfs-kernel-server
```

2. Share your home Documents to everyone. Edit /etc/exports and add
> /home/<your name>/Documents *(rw,insecure,no_subtree_check,async)
Then execute 
```
sudo exportfs -ra
```

3. Create a user directory in each machine
```
sudo mkdir -p /home/<spouse's user name>/Documents
sudo chmod -R 777 /home/<spouse>
```

4. Setup a mount point for the spouse's share. Edit /etc/fstab and add this line
> <remote workstation IP>:/home/<spouse>/Documents /home/<spouse>/Documents  nfs user,defaults 0 0

That's it !! The remote share should be mounted in your local /home/<spouse>/Documents. You can make symlinks from there to your own home directory for convenience. 

Why do we mount the remote share in /home instead of /mnt or /media? So that the pathnames remain the same, which means symlinks will works on both machines as well as any external document references (as long as they are in the Documents folder). You could also share the entire home directories with a few modifications.

Cheers!

---

### Post by Quarkrad on 2012-08-31
Thanks for your help.  My first problem is:

[B]dad@dadubuntu:~$ sudo mkdir -p /home/liz/Documents
dad@dadubuntu:~$ sudo chmod -R /home/liz 777
chmod: invalid mode: `/home/liz'
Try `chmod --help' for more information.
dad@dadubuntu:~$[/B] 

you were right, we both have an id of 1000.
note:  the directory /home/liz has been created.  At the moment the Documents folder in /home/liz has a padlock on it - I guess due to the permissions issue above.

---

### Post by LewisTM on 2012-08-31
Sorry, it should read
```
sudo chmod -R 777 /home/liz
```

---

### Post by 3rdalbum on 2012-08-31
What method have you tried before? As far as I recall, the Ubuntu wiki takes you through how to set up Samba using the smb.conf file - which is not conducive to getting a simple setup working within the space of two hours.

Oh, you can do it - but when I last set up my headless server I couldn't quite get it working right, and it literally took hours before it worked as expected.

For best results, install the system-config-samba package on the machine(s) to be used as server. This creates a new program called just "samba" which you will be able to access through the Dash. You can use this to set up some shared folders that anyone can read and write.

---

### Post by Quarkrad on 2012-08-31
Not sure if I can have both methods of working?  I have a question re both methods:

_LewisTM_

<remote workstation IP>:/home/<spouse>/Documents /home/<spouse>/Documents nfs user,defaults 0 0 

Does this mean each machine has to have a static/fixed ip?  I used to have this way of working but due to some troublesome Apple devices all pc's now have automatic ip selection on connection - so I don't have a fixed ip.  It looks to me that this method has to have a fixed ip per machine.  I could re-config.

_3rdalbum_

I have seen this window before (attached) - as I want to share my (/home/**dad**) Documents folder is it not the case that the user I want to allow access to my Documents folder is my spouse called **liz** (on the other pc).  If I tick **dad** in this window it seems to me that I'm allowing **dad** (that is me) access to my Documents folder - doesn't make sense to me.

---

### Post by LewisTM on 2012-08-31
> **Quarkrad said:**
> 
Does this mean each machine has to have a static/fixed ip?  I used to have this way of working but due to some troublesome Apple devices all pc's now have automatic ip selection on connection - so I don't have a fixed ip.  It looks to me that this method has to have a fixed ip per machine.  I could re-config.
Two methods of doing this:
1) A fixed IP can be configured with your router
2) Use a local hostname instead of IP. Type [FONT="Courier New"]hostname[/FONT] to get it, then append '.local'
So your fstab line would be 
> <remotehostname.local>:/home/<spouse>/Documents /home/<spouse>/Documents nfs user,defaults 0 0
You can [FONT="Courier New"]ping <hostname>.local[/FONT] to make sure it is reachable on the network. [FONT="Courier New"]avahi-browse -ar[/FONT] can also be informative.

---

### Post by Quarkrad on 2012-08-31
Thanks.  The result of my wifes hostname is: lizubuntu so my fstab looks like this:

[B]# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=903756de-cfba-405e-8d1d-c91fa9afc192 /               ext4    errors=remount-ro 0       1
UUID=09D6A06006C8DACD /media/store ntfs-3g defaults,uid=dad,gid=dad,dmask=002,fmask=113 0 0
UUID=53E871870E731F3D /media/backup ntfs-3g defaults,uid=dad,gid=dad,dmask=002,fmask=113 0 0
# swap was on /dev/sda5 during installation
UUID=9d21cf3a-d202-4f59-9cb7-497b390f52fb none            swap    sw              0       0
lizubuntu.local:/home/liz/Documents /home/liz/Documents nfs user,defaults 0 0 [/B]

The pc boots OK to the Desktop.  I can see the Documents folder when I look in **file system/home/liz/Documents**  but when I double click on it there are no files in it.

---

### Post by LewisTM on 2012-08-31
Was the NFS server installed and the share created on Liz's computer?

What do you get from these commands?
```
sudo mount lizubuntu.local:/home/liz/Documents /home/liz/Documents
showmount -e lizubuntu.local
```

---

### Post by Quarkrad on 2012-08-31
I've got it working now - many thanks for your help.  What I would like to do now is to access a top level folder called **Home** on one of my wife's ntfs partitions.  As far as her Ubuntu is concerned the folder is  **/media/homefiles/Home**.  It is unfortunate that I called this folder Home as it can be confused with Ubuntu's Home folder (it is a throw back to my pre Ubuntu days!).  This ntfs partition on my wife's machine is purely a storage partition where she keeps her data files.  Can you help with what I need to do re: etc/exports and fstab?  I believe the permissions on ntfs partitions need a level of expertise I do not have.

---

### Post by LewisTM on 2012-08-31
Glad it worked!
There is nothing preventing you from sharing any number of folders from any machine, including NTFS mounts. Just use the previous example as template, the basic idea is the same. The only difference is in a single parameter in the exports file:
> /media/homefiles/Home *(rw,insecure,no_subtree_check,**no_root_squash**,async)
You can create a local mount point anywhere on your computer for that share or recreate the directory /media/homefiles/Home if you prefer.

---

### Post by Quarkrad on 2012-09-01
Afraid I haven't quite got my head round this.  I've made the changes to my etc/export and fstab files - what do I have to do on my wifes machine to allow me to see her files?  For some reason I have two homefiles folders in /home/liz on my machine.  One has a lock icon on it the doesn't (both are empty).  

This is interesting (to me!) - because of the lock icon I've guess there's a permission issue so I tried  **sudo chmod -R 777 /home/liz** again on my pc.  Here is the terminal output.  It looks to me like all the sub folders and files in /media/homefiles/Home on my wife's pc are refusing me permission to access them.

[B]dad@dadubuntu:~$ sudo chmod -R 777 /home/liz
[sudo] password for dad: 
chmod: changing permissions of `/home/liz/Documents': Operation not permitted
chmod: changing permissions of `/home/liz/Documents/Personal Finances': Operation not permitted
chmod: cannot read directory `/home/liz/Documents/Personal Finances': Permission denied
chmod: changing permissions of `/home/liz/Documents/rsync': Operation not permitted
chmod: changing permissions of `/home/liz/Documents/code': Operation not permitted
chmod: changing permissions of `/home/liz/Documents/DerbyshireBS.pdf': Operation not permitted
chmod: changing permissions of `/home/liz/Documents/Mail Sound': Operation not permitted
chmod: changing permissions of `/home/liz/Documents/Mail Sound/gotmail16.wav': Operation not permitted
chmod: changing permissions of `/home/liz/Documents/Mail Sound/gotmail16.mp3': Operation not permitted
chmod: changing permissions of `/home/liz/Documents/graham.odt': Operation not permitted
chmod: changing permissions of `/home/liz/Documents/icons': Operation not permitted
chmod: changing permissions of `/home/liz/Documents/icons/firefox.jpeg': Operation not permitted
chmod: changing permissions of `/home/liz/Documents/icons/r5.jpeg': Operation not permitted
chmod: changing permissions of `/home/liz/Documents/icons/home.png': Operation not permitted
chmod: changing permissions of `/home/liz/Documents/icons/r4.jpeg': Operation not permitted
chmod: changing permissions of `/home/liz/Documents/Os Maps': Operation not permitted
chmod: cannot read directory `/home/liz/Documents/Os Maps': Permission denied
chmod: changing permissions of `/home/liz/Documents/freestyle4500.pdf': Operation not permitted
chmod: changing permissions of `/home/liz/Documents/wallpaper.jpg': Operation not permitted
chmod: changing permissions of `/home/liz/Documents/PanasonicFS11.pdf': Operation not permitted
chmod: changing permissions of `/home/liz/Documents/Sound Blaster.pdf': Operation not permitted
chmod: changing permissions of `/home/liz/Documents/fstab': Operation not permitted
chmod: changing permissions of `/home/liz/Documents/iancarinsurance.pdf': Operation not permitted
chmod: changing permissions of `/home/liz/Documents/urls': Operation not permitted
chmod: changing permissions of `/home/liz/Documents/Libreoffice Spell Check': Operation not permitted
chmod: changing permissions of `/home/liz/Documents/Passport Photos': Operation not permitted
chmod: cannot read directory `/home/liz/Documents/Passport Photos': Permission denied
chmod: changing permissions of `/home/liz/Documents/2003_focus_owner_guidemanual.pdf': Operation not permitted
chmod: changing permissions of `/home/liz/Documents/ubuntu tweaks': Operation not permitted
chmod: cannot read directory `/home/liz/Documents/ubuntu tweaks': Permission denied
dad@dadubuntu:~$ [/B]

---

### Post by LewisTM on 2012-09-01
You can't put the Homefiles mount point inside /home/liz/Documents because it already exists as a NFS mount point. You could put it as /home/liz/homefiles which is available. Then you just have to give full permissions to the mount point before you do the modifications in fstab.
```
sudo chmod 777 /home/liz/homefiles
```
Using the chmod -R command again was ill advised. The -R means recursive so it attempted to change all permissions on the subdirectories and files which are actually on the share! Thankfully NFS prevents that because it blocks access to the root (sudo) user.

---

### Post by Quarkrad on 2012-09-10
Alomst there I think but not quite.  I've attached a simple diagram so you can see my two pc and relevant info.  The set up on each pc is:

**dad  **
/etc/exports
/home/dad/Documents *(rw,insecure,no_subtree_check,async)
/media/store *(rw,insecure,no_subtree_check,no_root_squash,async)

/etc/fstab
192.168.1.4:/home/liz/Documents /home/liz/Documents nfs user,defaults 0 0 192.168.1.4:/media/homefiles /media/homefiles nfs user,defaults 0 0


**liz**
/etc/exports
/home/liz/Documents *(rw,insecure,no_subtree_check,async) 
/media/homefiles *(rw,insecure,no_subtree_check,no_root_squash,async)

/etc/fstab
192.168.1.5:/home/dad/Documents /home/dad/Documents nfs user,defaults 0 0 
192.168.1.5:/media/store /media/store nfs user,defaults 0 0 

On dad I have set up home/liz/Documents and home/liz/media/homefiles

I can go into home/liz/Documents on dad and see everything in Documents on liz's pc
But when I go into home/liz/media/homefiles on dad I see nothing

The same on liz's PC 
I can go into home/dad/Documents on liz and see everything in Documents on dad's pc
But when I go into home/dad/media/store on liz I see nothing

---

### Post by LewisTM on 2012-09-10
I'd like to see the NTFS partitions entries in you /etc/fstab files. 
For properly being exported by NFS, your entries should look like this:
> /dev/sd<something> /media/store ntfs defaults,uid=1000,gid=1000,umask=000,windows_names 0 0

---

### Post by Quarkrad on 2012-09-10
This is what my fstab files looks like:

[B]# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=903756de-cfba-405e-8d1d-c91fa9afc192 /               ext4    errors=remount-ro 0       1
UUID=09D6A06006C8DACD /media/store ntfs-3g defaults,uid=dad,gid=dad,dmask=002,fmask=113 0 0
UUID=53E871870E731F3D /media/backup ntfs-3g defaults,uid=dad,gid=dad,dmask=002,fmask=113 0 0
# swap was on /dev/sda5 during installation
UUID=9d21cf3a-d202-4f59-9cb7-497b390f52fb none            swap    sw              0       0
#lizubuntu.local:/home/liz/Documents /home/liz/Documents nfs user,defaults 0 0
#lizubuntu.local:/home/liz/homefiles /media/homefiles nfs user,defaults 0 0

192.168.1.4:/home/liz/Documents /home/liz/Documents nfs user,defaults 0 0 
192.168.1.4:/media/homefiles /media/homefiles nfs user,defaults 0 0[/B]

you will note that originally I used your lizubuntu.local format but I have taken these out as I have gone back to static ip addresses for each machine.

---

### Post by LewisTM on 2012-09-10
We might be going into uncharted territory here since I don't have an NTFS partition to test this.
Try editing your NTFS entry to look like this:
```
UUID=09D6A06006C8DACD /media/store ntfs defaults,uid=dad,gid=dad,umask=000 0 0
```
Reboot and try again to read the NTFS export.
You don't have to switch seats with liz's, you can test it locally 
```
sudo chmod 777 /mnt
sudo mount localhost:/media/store /mnt
ls /mnt
```

---

### Post by Quarkrad on 2012-09-11
Not quite there.  I did your changes and it looked OK - the termainal output showed the contents of my **store** folder.  I rebooted and have the same problem - each user can see/read the other persons Documents folder but neither can see the /media/.....  folder.  On dad's machine /media/store is on a ntfs partition but on liz's machine her /media/homefiles is on a ext4 partition.  Here are the fstab outputs from each machine.

**dad**
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# Ubuntu partition sda2  ext4
UUID=903756de-cfba-405e-8d1d-c91fa9afc192 /               ext4    errors=remount-ro 0       1
# /media/store sda3  ntfs
UUID=09D6A06006C8DACD /media/store ntfs defaults,uid=dad,gid=dad,umask=000 0 0
# /media/backup sb5  ntfs
UUID=53E871870E731F3D /media/backup ntfs-3g defaults,uid=dad,gid=dad,dmask=002,fmask=113 0 0
# swap
UUID=9d21cf3a-d202-4f59-9cb7-497b390f52fb none            swap    sw              0       0


192.168.1.4:/home/liz/Documents /home/liz/Documents nfs user,defaults 0 0 
192.168.1.4:/media/homefiles /media/homefiles nfs user,defaults 0 0

**liz**
/dev/fd0 /media/floppy0 vfat noauto 0 0 
# ubuntu sda1* ext4 
UUID=1c3bfce5-4bde-40df-a04d-714f95e2415b / ext4 defaults 0 1 
# swap 
UUID=33729fc7-e436-4a9f-a7a1-00293f4deeb2 swap swap sw 0 0 
# /media/homefiles sda5 ext4 
UUID=ae207b6d-9c06-4865-b0a4-4f3f16f60e25 /media/homefiles ext4 deaults 0 0 
/dev/sda5 /media/homefiles ext4 defaults 0 2 
# /media/backup* sdb1* ntfs 
UUID=6B09676C1816B614 /media/backup ntfs-3g defaults 0 0 
192.168.1.5:/home/dad/Documents /home/dad/Documents nfs user,defaults 0 0 
192.168.1.5:/media/store /media/store nfs user,defaults 0 0

---

### Post by LewisTM on 2012-09-11
You are right, this should be simple :)

In liz's fstab there is a typo for the ext4 partition: "deaults". Not sure if that could explain anything.

I just made some test sharing an NTFS partition with bare defaults for both fstab and exports config files. Everything works out of the box, no fancy parameter required (not even no_root_squash).

Do you mean that on each machine you can mount the /media/... share locally but not from the remote peer?

Can you post the output of:
On **dad**
```
mount
sudo mount 192.168.1.4:/media/homefiles
```

On **liz**
```
mount
sudo mount 192.168.1.5:/media/store
```
EDIT: I also just saw typos in both of your exports files, in the /media entries: "asyn c"

---

### Post by Quarkrad on 2012-09-12
I have corrected the **deault** typo in liz's fstab

Sorry - I didn't really understand your comment on the typo ...in the /media entries: "asyn c"....  I have checked the exports files on both machines and they look alright.  E.G in dad it reads:

[B]/home/dad/Documents *(rw,insecure,no_subtree_check,async) 
/media/store *(rw,insecure,no_subtree_check,no_root_squash,async)[/B] 

there are no gaps/spaces between the characters.

The output of the commands are:

[B]dad@dadubuntu:~$ sudo mount 192.168.1.4:/media/homefiles 
mount.nfs: /media/homefiles is busy or already mounted 
dad@dadubuntu:~$ 


liz@lizubuntu:~$ sudo mount 192.168.1.5:/media/store 
[sudo] password for liz: 
mount.nfs: /media/store is busy or already mounted 
liz@lizubuntu:~$ [/B]


Could it be somethings stupid (me being stupid!) like the way I have created the folders on each machine?  e.g. on dad I have created:

/home/liz/Documents      I can read liz's remote Documents file from dad's machine
/home/liz/media/homefiles   I cannot read this remote folder on liz's machine

So at the top level I have:

home/dad/Desktop, Downloads, Documents, Pictures, etc  (normal ubuntu structure)
home/liz/Documents
home/liz/media/homefiles

---

### Post by Morbius1 on 2012-09-12
@Quarkrad,

I don't use NFS so I can't be of any assistance on that front but I do have a request. Could you please go to your first post and change the title to:
> NFS,  This is (frustratingly) Simple - Apparently!Every morning I see this post and every morning I want to answer it before realizing it's become an NFS question.

If you want to explore a Samba solution I would think creating a separate topic would be better since it will avoid the " Samba between Linux machines is for men without the capacity to reproduce" syndrome that can happen when NFS and Samba are mentioned in the same topic. ;)

---

### Post by nothingspecial on 2012-09-12
Thread title changed at the request of the OP.

---

### Post by LewisTM on 2012-09-12
Back to the topic.
I'm slowly running out of ideas.
Funny that you mention there is no typo then you paste the line again
> /media/store *(rw,insecure,no_subtree_check,no_root_squash,[COLOR="Red"]asyn c[/COLOR]) 
So the share appears to get mounted. I didn't get the output of the [FONT="Courier New"]mount[/FONT] command as requested. Just type [FONT="Courier New"]mount[/FONT] and post the line about nfs.
I'm discarding NTFS as the source of the problem since an ext4 share also fails to work. And you don't get any Permission error, but no file is listed. I just sounds like your share doesn't get mounted.
Please also post the outputs of commands:
```
showmount -e 192.168.1.4
showmount -e 192.168.1.5
```
Thanks!

---

### Post by Quarkrad on 2012-09-13
These are the outputs of the commands:


dad@dadubuntu:~$ mount
/dev/sda2 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda3 on /media/store type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb5 on /media/backup type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
rpc_pipefs on /run/rpc_pipefs type rpc_pipefs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
gvfs-fuse-daemon on /home/dad/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dad)
192.168.1.4:/home/liz/Documents on /home/liz/Documents type nfs (rw,user=root,noexec,nosuid,nodev,vers=4,addr=192.168.1.4,clientaddr=0.0.0.0)
192.168.1.4:/media/homefiles on /media/homefiles type nfs (rw,user=root,noexec,nosuid,nodev,vers=4,addr=192.168.1.4,clientaddr=0.0.0.0)
dad@dadubuntu:~$ 

dad@dadubuntu:~$ showmount -e 192.168.1.4
Export list for 192.168.1.4:
/media/homefiles    *
/home/liz/Documents *
dad@dadubuntu:~$ 

dad@dadubuntu:~$ showmount -e 192.168.1.5
Export list for 192.168.1.5:
/media/store        *
/home/dad/Documents *
dad@dadubuntu:~$

---

### Post by Quarkrad on 2012-09-13
It's working!!!!  Many many thank for all your hard work - I do appreciate it.  The problem, my end, was looking in the wrong place. I have been trying to follow your thoughts/suggestions and working out what was going on - my clue was: 

[B]/home/liz/Documents *(rw,insecure,no_subtree_check,async)
/media/homefiles *(rw,insecure,no_subtree_check,no_root_squash,async)[/B] 

To look at these files I created /home/dad/liz/Documents which worked - but I couldn't work out how the folder I created /home/liz/homefiles related to the line:

/media/homefiles *(rw,insecure,no_subtree_check,no_root_squash,async)

so in Nautilus I looked in file system/media/ and saw a folder called homefiles!

So to access the homefiles folder on liz I (that is dad) have to look in file system/media/homefiles.   I was looking in the wrong place all the time.  Again, thank you for your help - I've managed to tidy up the fstab files on both machines as well.

---

### Post by LewisTM on 2012-09-13
Great!!
You could make a symbolic link to /media/homefiles and place it in your Home folder for convenience.

Please mark as SOLVED

---

