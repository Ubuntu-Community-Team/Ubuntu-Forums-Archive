---
title: "reformatted iomega prestige usb hard drive but can't create folders/save data"
date: 2010-03-05
forum: General Help
---

### Post by PublikDefender on 2010-03-05
Used gparted to format a brand new iomega prestige 1 tb usb hard drive (ntfs) to ext4. The problem is that I can't create folders from nautilus because I don't have permission (root). There is one folder present already lost + found that appeared after reformatting. i can't access that folder because of permissions. Was any of this supposed to happen after formatting an external drive and how can I fix this? I intend to use grsync to back up important folders but can't create folders from grsync also.  Thanks for your help.

note: the only account on ubuntu is mine and i have access to root privileges
update: added a screenshot but i am not sure what screenshots you guys need to help. i can take more if you have any requests.

---

### Post by PublikDefender on 2010-03-05
I added a second screenshot of what happens when I show the permissions info for the hard drive.  Again, I'm not even sure this is where the problem lies. I just want to create folders for various media and use grsync to back up important folders.

---

### Post by HermanAB on 2010-03-05
Howdy,

The initial disk permissions are set by the mount command (read man mount).  If a disk is mounted read only, then you cannot change anything with chmod or chown, you have to remount the disk with the correct permissions first.

---

### Post by darolu on 2010-03-05
You need to add permissions to it using your fstab file, mount your hard drive and open your terminal (Aplications - Accessories - Terminal) and type this in:
```
$ blkid
```
It will print a series of UUIDs, corresponding to your hard drive partitions, copy/write down the one corresponding to your external hard drive, we'll use that number later.

Now you need to create a mount point for your drive, in your terminal:
```
$ sudo mkdir /media/<mountpoint>
```
Sustitute <mountpoint> for whatever you like.

Now add your drive to your fstab file (with its permissions) type this in your terminal:
```
$ gksu gedit /etc/fstab
```

At the end of the file, add this lines:
```
#External hard drive.
UUID=<UUIDnumber>	/media/<mountpoint>	ext4	defaults,user,exec,rw	0	0
```
Save your file, and that's it.

---

### Post by PublikDefender on 2010-03-05
When I type blkid in terminal nothing happens. The next line is $.
$ blkid
$ 

I also unmounted the drive, and then remounted but still don't get anything from blkid.
I then tried cat /etc/fstab but it doesn't seem to show the hard drive:

user1@user1-deus:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=22ddea6d-0ad0-40e7-be68-e281c5f5b27f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=07a32f7d-fb84-40fb-ba5a-5b382056a6bf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
user1@user1-deus:~$

---

### Post by darolu on 2010-03-05
Oh my bad, you must run blkid with sudo:
```
$ sudo blkid
```
It should print something like this:
```
dan@danbuntu:~$ sudo blkid 
[sudo] password for dan: 
/dev/sda2: UUID="75670437-949c-48ee-97e8-641633ece53a" TYPE="swap" 
/dev/sda1: UUID="400AA41B7790B28A" LABEL="Winbugs" TYPE="ntfs" 
/dev/sda5: UUID="7bf127fb-aa85-4bb1-bb38-c32bef9be900" TYPE="ext4" 
/dev/sda6: LABEL="Linuxhome" UUID="cf396376-a6f1-456d-bd37-17dd36922f25" TYPE="ext4" 
/dev/sdb1: UUID="**49B723546D64AA24**" LABEL="Pato" TYPE="ext2"
```
Suppose your hard drive is /dev/sdb1 just like my "Pato" one, then you must add this to your fstab file:
```
...
# swap was on /dev/sda5 during installation
UUID=07a32f7d-fb84-40fb-ba5a-5b382056a6bf none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

#External hard drive.
UUID=**49B723546D64AA24**	/media/pato	ext2	defaults,user,exec,rw	0	0
```
Don't forget to create the mount point first; in my example "/media/pato" (also my example is ext2, you have to use your file system [ext4]).

---

### Post by PublikDefender on 2010-03-05
ok, i followed those steps exactly.
I am getting the error message:

                                 Unable to mount i9

 Error mounting: mount exited with exit code 1: helper failed with:
 mount: /dev/sdb1 already mounted or /media/h8 busy
 
Also, the computer appears to be reading the hard drive twice. the "new" drive is called h8 and always appears under places in the ubuntu menu. the old drive i9 only appears when i plug the drive in and immediately goes to the unable to mount i9 error.

when i first formatted the drive i used the directions here:
[http://www.mattcutts.com/blog/format-external-drive-for-linux/](http://www.mattcutts.com/blog/format-external-drive-for-linux/)

one of the steps i originally followed was:

mount
sudo apt-get install e2fsprogs
sudo e2label /dev/sdf1
sudo e2label /dev/sdf1 &#8220;M1&#8243;
sudo e2label /dev/sdf1 

this is why the drive got labeled i9 (and my drive is actually sdb1). do you think this has something to do with the errors I am having now? can i start from scratch and reformat the whole drive again? what would i have do before starting over?

Update: I tried something else. I renamed the i9 drive to h8 using the command:
sudo e2label /dev/sdb1 "h8" 
However, I am still getting the same errors except now "both" drives are called h8.

---

### Post by nothingspecial on 2010-03-05
unmount the drive
```

sudo e2label /dev/sd?? new_name
```

unplug then plug it back in```


sudo chown -R yourusername:yourusername /media/new_name
```

You don`t have to relabel it although it sounds like you want to.

EDITED DUE TO INCORRECT INSTRUCTIONS

---

### Post by PublikDefender on 2010-03-05
it's not that I want to rename anything. i can't mount the drive or access it.

another error i get is when i try to "remove the drive safely":
Unable to stop drive
Failed to eject media. One or more volumes on the media are busy.

after i then unplug the drive and plug it back in later, the second h8 drive icon appears on the desktop. after I am unable to create a folder in that drive, i try to unmount it and get the error:
Unable to unmount the location.
unmount: /media/h8 mount disagrees with the fstab

So to sum up the errors:
1. the new h8 icon is in the places menu all the time.
2. i plug in the external drive.
3. another h8 icon shows up in "places" as well as desktop, but an error occurs.
4. next, if you click on the old h8 icon you get: Unable to mount h8. mount: /dev/sdb1 already mounted or /media/h8 busy. mount: according to mtab, /dev/sdb1 is already mounted on /mediia/h8
5. Then if I try to unmount the newer h8 icon i get the error: unable to unmount h8. Device is not mounted.
6. And then I can't remove device safely.

---

### Post by nothingspecial on 2010-03-05
Put a # infront of any line reffering to it in etc/fstab then reboot with it unplugged. Then plug it back in.

It should auto mount, then change the ownership to you with the chown command.

---

### Post by PublikDefender on 2010-03-05
so to be clear, do you still want me to do:


sudo e2label /dev/sd?? new_name
sudo chown -R /media/new_name


and do you want me to choose a new name entirely for both? or do the chown command only? and then at what point do you want me to take the fstab line out of comments (#)?

---

### Post by nothingspecial on 2010-03-05
Not if you don`t want to. I just want you to be sure which drive you are chowning.

---

### Post by nothingspecial on 2010-03-05
Sorry, that wasn`t very clear.
```

sudo chown -R yourusername:yourusername /media/whatever_your_drive_is_called
```

is the correct syntax.

And you comment out the fstab before that and reboot.

Changing the label is up to you

---

### Post by darolu on 2010-03-05
> **PublikDefender said:**
> ok, i followed those steps exactly.
I am getting the error message:

                                 Unable to mount i9

 Error mounting: mount exited with exit code 1: helper failed with:
 mount: **/dev/sdb1 already mounted **or /media/h8 busy
 
Also, the computer appears to be reading the hard drive twice. the "new" drive is called h8 and always appears under places in the ubuntu menu. the old drive i9 only appears when i plug the drive in and immediately goes to the unable to mount i9 error.

when i first formatted the drive i used the directions here:
[http://www.mattcutts.com/blog/format-external-drive-for-linux/](http://www.mattcutts.com/blog/format-external-drive-for-linux/)

one of the steps i originally followed was:

mount
sudo apt-get install e2fsprogs
sudo e2label /dev/**sdf1**
sudo e2label /dev/**sdf1** &#8220;M1&#8243;
sudo e2label /dev/**sdf1** 

this is why the drive got labeled i9 (and my drive is actually sdb1). do you think this has something to do with the errors I am having now? can i start from scratch and reformat the whole drive again? what would i have do before starting over?

Update: I tried something else. I renamed the i9 drive to h8 using the command:
sudo e2label /dev/sdb1 "h8" 
However, I am still getting the same errors except now "both" drives are called h8.

You have to make sure your hard drive is /dev/**sdb1** or if it is /dev/**sdf1**. If you have more hard drives than your primary one (the one with your Ubuntu) and your external, this can be a problem.

With the instructions I gave you, it will be mounted automatically if you turn your computer on with the hard drive plugged and ON. It is normal that you see the drive listed twice under the Places menu or under a Nautilus window, you can easily identify which one is the working one by the little umount icon (a little arrow pointing up), clicking on it should give you access to your hard drive so you can write files in it.

Just to make sure your hard drive is /dev/sdb1 and you used the correct UUID, open a terminal and run:
```
$ sudo fdisk -l
```
And paste your result, (btw it is a lower case "L").

Changing the owner:group with chown as some people are suggesting won't work as the /dev list is filled (and therefore reset) every time you turn on your computer or when you plug your hard drive when it is already on.

---

### Post by PublikDefender on 2010-03-05
user1@user1-deus:~$ sudo fdisk -l
[sudo] password for user1: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x50000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29272   235127308+  83  Linux
/dev/sda2           29273       30401     9068692+   5  Extended
/dev/sda5           29273       30401     9068661   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcbce2081

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux
user1@user1-deus:~$ 

darolu, here is what sudo fdisk -l looks like, so it appears sdb1 is the intended drive. I did turn off my laptop first, and then plugged in and turned on the hard drive. However, I still can't create files/folders in the drive. Having the hard drive connected and on before turning on the computer did take away those mount error messages/dialog boxes though.

---

### Post by PublikDefender on 2010-03-06
OK, so I commented out the fstab line referring to that drive, then i restarted the laptop.  After the re-boot I turned on the drive and plugged it in. it auto-mounted.

then i did:
sudo chown -R user1:user1 /media/h8

Then I restarted the laptop.  But the permissions didn't change and I can't make folders.

I can't think of anything I did wrong.  When I added # to comment out the line in fstab, the drive wasn't attached. that's correct, right?  also, am I supposed to remove the # from that fstab line now? i didn't do that because it wasn't explicitly stated.

Note: I tried both darolu and nothingspecial approaches at different times, so that one approach would not screw up the other. first, i did all of darolu's steps up to and including my last post. then i did nothingspecial's approach detailed here a later time.

---

### Post by PublikDefender on 2010-03-10
bump

---

### Post by PublikDefender on 2010-03-10
bump.
it's just a hard drive please help. it is a brand new drive so i don't care about losing data. i can start over with new suggestions if you like.

---

### Post by nothingspecial on 2010-03-11
Reformat it. The trick is to make sure you own it after you do.

Because root has to format it root will own it. So after you have formatted it, mount it and use the chown command to give you ownership of it.

---

### Post by PublikDefender on 2010-03-11
after reformatting:

user1@user1-deus:~$ sudo chown -R user1:user1 /media/sdb1   [sudo] password for user1:  
 chown: cannot access `/media/sdb1': No such file or directory  
 user1@user1-deus:~$ sudo chown -R user1:user1 /media/sdb1  
 chown: cannot access `/media/sdb1': No such file or directory  
 user1@user1-deus:~$ sudo chown -R user1:user1 /media/h8  
 user1@user1-deus:~$ 

then I "safely remove drive" unplugged it rebooted and plugged it back in and still couldn't transfer any data.
I then used the chown command again, unmounted, "safely removed drive", unplugged drive, plugged drive back in (without rebooting this time) and still could not copy data.
I then used the chown command again, unmounted, did not unplug drive, mounted drive, and could not copy data.

---

### Post by nothingspecial on 2010-03-11
Try ```
chmod -R 775 /media/h8
```

---

### Post by PublikDefender on 2010-03-11
unfortunately, that didn't work.

---

### Post by scouser73 on 2010-03-12
**1** - Go to **Terminal**, copy & paste this command: **gksudo nautilus** that will open Terminal as root

**2** - Navigate to your  folder/file/drive, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your folder/file/drive.

---

### Post by PublikDefender on 2010-03-12
scouser73,

it worked! thanks a million! i tested the hard drive upon reboot and the permissions were kept to the user specified. so all is well.

quick question though. i noticed a few errors when i opened nautilus as root. was this supposed to happen:

                                 user1@user1-deus:~$ gksudo nautilus  
 Initializing nautilus-gdu extension  
 

 ** (nautilus:4183): WARNING **: No marshaller for signature of signal 'UploadFinished'  
 

 ** (nautilus:4183): WARNING **: No marshaller for signature of signal 'DownloadFinished'  
 

 ** (nautilus:4183): WARNING **: No marshaller for signature of signal 'ShareCreateError'  
 Initializing nautilus-open-terminal extension  
 Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory  
 Please ask your system administrator to enable user sharing.  
 

 

 --- Hash table keys for warning below:  
 --> l2065  
 --> inode/directory  
 --> root  
 --> user1  
 --> l2049  
 Shutting down nautilus-open-terminal extension  
 Shutting down nautilus-gdu extension  
 

 (nautilus:4183): Eel-WARNING **: "unique eel_ref_str" hash table still has 5 elements at quit time (keys above)  
 

 (nautilus:4183): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 4 elements at quit time  
 user1@user1-deus:~$

---

### Post by PublikDefender on 2010-03-12
Nothingspecial & Darolu,

I also just wanted to send you guys a shout out for helping me out over the past week. I appreciate the help you guys have given me.

---

### Post by nothingspecial on 2010-03-14
> **PublikDefender said:**
> Nothingspecial & Darolu,

I also just wanted to send you guys a shout out for helping me out over the past week. I appreciate the help you guys have given me.

I`m just glad you got it sorted. Cheers Scoucer! (As a born, bred, dyed in the wool manc, it feels strange typing that ;))

---

