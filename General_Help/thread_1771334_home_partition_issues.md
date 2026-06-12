---
title: "/home partition issues"
date: 2011-05-30
forum: General Help
---

### Post by motherboyxx on 2011-05-30
I tried searching this and i am sure my search parameters were poor because this has to have happened before. 

So I set up natty with a fresh install and created a /home partition of 310GB and /_ partition of 10GB (i know thats allot) using psychocats.net tutorial. I have been using it for a bit now and just realized my "home" folder is still in the 10GB partition.

I can manually move files over to the 310GB and use it like a back up (similar to D drive in windows).  What I would like to do is set up the 310GB to be the default location for home and all my files.  See pictures below. Does this have to do with both partitions being ext4? Thanks in advance

---

### Post by hwttdz on 2011-05-30
I think by /_ you mean / (also called root) and I wouldn't say 10gb is a lot for root.  In fact many people would say it's very little (I think it's probably a fine amount if you don't plan on installing every program around).  

Yes you can move your home partition.  You'll need to copy your home directory over to that drive, I probably reformat that drive, and then "sudo cp -r /home/username /path/to/big/drive".  Then you'll update fstab either by hand, or using one of the graphical interfaces, such as pysdm and make the mount point of the big drive /home.  Then you can reboot and your home drive will be on the big disk.  You can probably do this without a restart, but I am not quite as averse to restarting as some folk.  

I'd recommend either reading up some on fstab/partitions or waiting for another response before following my instructions, as any time you use sudo (as you'll have to to change the fstab, if not other things as well) you risk seriously messing up your system.

Also the smart status of that disk says it's not in perfect health.  So you may even want to consider getting a second HDD and moving your home to that.

---

### Post by LowSky on 2011-05-30
My root is only 12GB and my home is 20.

I then have links to folders for my videos and music as those directories hold terabytes of data.

what would be easier is start the pc with the live cd... run the live mode...  open gparted. from gparted you can resize the partitions.

make backups of data before doing anything

---

### Post by ratcheer on 2011-05-30
I did pretty much the same thing, just yesterday. Here is my thread. If you need more details, just ask.

[http://ubuntuforums.org/showthread.php?t=1770487](http://ubuntuforums.org/showthread.php?t=1770487)

Tim

---

### Post by motherboyxx on 2011-05-30
> **ratcheer said:**
> I did pretty much the same thing, just yesterday. Here is my thread. If you need more details, just ask.

[http://ubuntuforums.org/showthread.php?t=1770487](http://ubuntuforums.org/showthread.php?t=1770487)

Tim

LOL...i do indeed need more details.  Specifically;  I reformatted the partition, gave it a more intuitive label and copyed my home directory to it.  Now I want to make that /dev/sda5 the "default" location for the Home file tree, instead of the /dev/sda1.  Again thanks for helping a beginner.

---

### Post by oldfred on 2011-05-30
these are three versions of moving /home to another partition. They are essentially identical but using different commands for the copy. See which makes more sense to you.

Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership
To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by ratcheer on 2011-05-30
> **motherboyxx said:**
> LOL...i do indeed need more details.  Specifically;  I reformatted the partition, gave it a more intuitive label and copyed my home directory to it.  Now I want to make that /dev/sda5 the "default" location for the Home file tree, instead of the /dev/sda1.  Again thanks for helping a beginner.

Is /dev/sda5 currently mounted? If yes, what is the top-level directory name?

Tim

---

### Post by motherboyxx on 2011-05-30
> **ratcheer said:**
> Is /dev/sda5 currently mounted? If yes, what is the top-level directory name?

Tim
/media/

If i open the disk utility before I access the partition it states it is unmounted.  I can of course mount it with the utility or by accessing it from "places" on the desktop; from which I am told it is "mounted at /media/mainspace"

---

### Post by ratcheer on 2011-05-30
Ok, then first you meed to get it mounted "normally".

1) sudo blkid

Note the uuid of /dev/sda5.

2) sudo vi /etc /fstab

(Or, use whatever text editor you prefer). Copy the line for / to a new line. Edit the new line to make the uuid what you found in step 1. Change / to /mainspace

3) Reboot. You should come up with a mounted filesystem at /mainspace. Run "df -Th" and post the output. If everything looks good, we will swap it with your /home, later.

Tim

---

### Post by motherboyxx on 2011-05-30
Following the official ubuntu documentation listed above this is what I did, below is terminal output.


dan@dan-Inspiron-1545:~$ sudo blkid
[sudo] password for dan: 
/dev/sda1: UUID="e1c80579-0d2b-45ff-96e5-831c7bedb748" TYPE="ext4" 
/dev/sda5: LABEL="Mainspace" UUID="bd2e08e1-ba0a-4ecb-9746-757ed9604bb4" TYPE="ext4" 
dan@dan-Inspiron-1545:~$ sudo cp /etc/fstab /etc/fstab.$(date +%2011-%05-%30)
cp: target `%30' is not a directory
dan@dan-Inspiron-1545:~$  sudo cp /etc/fstab /etc/fstab.$(date +%Y-%m-%d)
dan@dan-Inspiron-1545:~$ cmp /etc/fstab /etc/fstab.$(date +%Y-%m-%d)
dan@dan-Inspiron-1545:~$ gksu gedit /etc/fstab

                    
(gedit:1918): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.1X5DWV': No such file or directory

(gedit:1918): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:1918): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.NGBLWV': No such file or directory

(gedit:1918): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
dan@dan-Inspiron-1545:~$ 
dan@dan-Inspiron-1545:~$ **$sudo mkdir /mnt/newhome**
mkdir: cannot create directory `/mnt/newhome': Permission denied
dan@dan-Inspiron-1545:~$ 

Here is the fstab editor output. 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=e1c80579-0d2b-45ff-96e5-831c7bedb748 /               ext4    errors=remount-ro 0       1
# (**identifier)  (location, eg sda5)   (format, eg ext3 or ext4)      (some settings) **
UUID=bd2e08e1-ba0a-4ecb-9746-757ed9604bb4   /media/home    ext4          nodev,nosuid       0       2 

I bolded the area of the fstab editor/terminal that i think/know i messed up (blindly copying and pasting). 

I am reading back and forth from different tutorials and i think i am just confusing myself.  Any help is still needed

---

### Post by ratcheer on 2011-05-30
Ouch. We both posted at the same time.

I can try to help for a while. Run "df -Th" and post the output.

Tim

---

### Post by dFlyer on 2011-05-30
Your /home folder is still under /. When you created your / as 10 gigs, which is about right for /. After that did you create another partition and assign it as /home with the rest of your free space?

---

### Post by motherboyxx on 2011-05-31
> **dFlyer said:**
> Your /home folder is still under /. When you created your / as 10 gigs, which is about right for /. After that did you create another partition and assign it as /home with the rest of your free space?

Thats what I thought I did.  Its seemed straight forward enough when i did it. df -Th output below

dan@dan-Inspiron-1545:~$ df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda1     ext4    9.2G  4.4G  4.4G  50% /
none      devtmpfs    2.0G  680K  2.0G   1% /dev
none         tmpfs    2.0G  1.6M  2.0G   1% /dev/shm
none         tmpfs    2.0G   96K  2.0G   1% /var/run
none         tmpfs    2.0G     0  2.0G   0% /var/lock
/dev/sda5     ext4    285G  1.1G  269G   1% /media/home

my /home is right there on the /sda5 partition so unless I fixed it in my sleep I am unsure of why my files are saving under the /sda1 partition.  I appreciate all your help guys

---

### Post by ratcheer on 2011-05-31
Ok, you are almost there.

1) mv /home /home_old

2) mv /media/home /home

3) Edit /etc/fstab to change the line for /dev/sda5 to be mounted at /home

Reboot and it should come up the way you want it.

Tim

---

### Post by motherboyxx on 2011-05-31
> **ratcheer said:**
> Ok, you are almost there.
 
1) mv /home /home_old
 
2) mv /media/home /home
 
3) Edit /etc/fstab to change the line for /dev/sda5 to be mounted at /home
 
Reboot and it should come up the way you want it.
 
Tim
 # **(identifier) (location, eg sda5) (format, eg ext3 or ext4) (some settings) **
UUID=bd2e08e1-ba0a-4ecb-9746-757ed9604bb4 /media/home ext4 nodev,nosuid 0 2 

Just to confirm since I am at work and cannot do this till I get home tonight but step 3 I should just change UUID=******/media/home to the new mount point of UUID=*****/home
 
Just remove the /media/ ?

---

### Post by ratcheer on 2011-05-31
No, no, no.

The UUID of /dev/sda5 should not be changed. It is the mount point you are changing, from /media/home to /home. Follow my instructions from my prior post (#14).

Tim

PS - Sorry. Maybe that is what you mean. Yes, on the fstab line for /dev/sda5, where the mount point is currently "/media/home", just change that to "/home".

---

### Post by motherboyxx on 2011-05-31
Thanks guys for all the help.  I just backed up my data and ran the fstab editor and remounted /media/home to just /home. All seems to be working now as should be. I tried mv/home/home_old  and I got an error message saying I could not do that.  So i just backed up the data and changed the mount point for that partition.

---

### Post by ratcheer on 2011-05-31
Excellent. After things work for a while, you can just delete the old home directory. You may need to do it with root permissions (sudo).

Tim

---

