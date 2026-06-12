---
title: "Splitting home directory"
date: 2011-07-24
forum: General Help
---

### Post by seak1 on 2011-07-24
Hi, I'm new to ubuntu (installed 3 days ago).

I have two disks in my notebook - one hdd (big, 320GB) and one ssd (very fast, 120GB). Everything is on ssd now, but I want to know how can I split my home directory to make config folders (like .thunderbird, .mozilla, .purple) to use ssd (for very fast response), and put movies, pictures, downloads and other folders to use hdd (a lot of space). Simply mounting hdd as /home is not a good option, becouse config files would be on hdd also.

Should I mount (or link) all folders like /home/username/Videos to hdd, or is there a better solution?

---

### Post by mikewhatever on 2011-07-24
Move all data folders from the ssd to the hdd, and then create links to them in your home folder. Creating links is easy, just right click a folder and select 'Make link'.

Edit: If you find that the default directories are recreated on reboot, edit .config/user-dirs.dirs and comment them out.

---

### Post by bodhi.zazen on 2011-07-24
Yes, best option is to use a link as you suggest.

---

### Post by oldfred on 2011-07-24
After you copy all your data folders like Music to the partition on your other drive.
Unmount your temporary mount if it is just temporary.

NOTE: The mount point can be anywhere. If it's in your /home or /media folders it will show up under "Places". If it's directly off "/" or /mnt it will not. I prefer /mnt so I do not see it other than thru the links.

sudo mkdir /mnt/data
sudo chown $USER:$USER /mnt/data
#sudo chmod 766 /mnt/data
#OR - The big "X" will also not make files executable unless they were executable to begin with.
sudo chmod -R a+rwX /mnt/data
# find your UUID
sudo blkid
#Edit fstab with your UUID, use ext3 or ext4 depending on format:
gksudo gedit /etc/fstab
UUID=a55e6335-616f-4b10-9923-e963559f2b05  /mnt/data    ext3         auto,users,rw,relatime               0  2 
#Verify entry is ok, if no errors it is:
sudo mount -a
#from home so default location of link is in /home/$USER
# cannot have duplicate entries, so move current to temporary location, repeat for each folder you want to move.
mv Music oldMusic
# Music is then also the folder in the partition mounted as /mnt/data
ln -s /mnt/data/Music
#Or link all folders with one command:
for i in `echo /mnt/data/*`;do ln -s $i; done

You can delete oldMusic after you confirm everything is ok.

---

### Post by Morbius1 on 2011-07-24
My personal preference ( not that anyone's asked ) is to use bind. Probably because I share a lot of my folders with Samba across the network and Samba can't follow symlinks.

Let's say your second disk is mounted in fstab as /Data. Then copy all of the home folders you want to /Data. Then use the following command to bind the folders in /Data back to the home folder:
```
sudo mount --bind /Data/Videos /home/morbius/Videos
```You've got 3 options to have this all happen automatically:

[1] Stick that same expression in /etc/rc.local right above the "exit 0" line.

[2] Back in the good old days you could add it to fstab but that doesn't work anymore - well, it works in Debian just not in Ubuntu. The syntax changes though:
```
/Data/Videos /home/morbius/Videos auto bind 0 0
```You just had to make sure you place that line after the fstab line that mounts /Data itself.

[3] Create an upstart job that will execute the "mount --bind" only after mountall is complete. This is that way I do it these days.

Either way you have to make sure you are auto mouning /Data in fstab.

---

### Post by seak1 on 2011-07-24
Thank you very much :)

---

### Post by Derek Karpinski on 2011-08-17
> **Morbius1 said:**
> My personal preference ( not that anyone's asked ) is to use bind. Probably because I share a lot of my folders with Samba across the network and Samba can't follow symlinks.
 
In smb.conf:
 
```
follow symlinks = yes
wide symlinks = yes
unix extensions = no
```
 
Will fix that.

---

### Post by arodulfo on 2012-12-21
I have reused a 350 GiB hdd (after moving all the important files to a backup USB HDD) to introduce Ubuntu in my home main computer.

I specifically told the installer to use some 50 GiB for "/" mountpoint (ext4), some 4 GiB for swap and the rest of it for "/home" mountpoint (ext4 as well). 
I did assume the system would place my $HOME folders and files under the "/home" mountpoint, so I kept installing applications to get the system closer to what I need.

To my surprise, I found my $HOME folder is located in the small partition I wanted to devote for / and /boot, with almost nothing inside the equivalent folder in the bigger partition.

I have closely followed your comprehensive explanation on how to get the system refer to the files wherever you may want the to be; however, I wonder why didn't the system perform as expected on installation time?

I have almost no new data in the new disk: I installed Ubuntu on it last week. Of course I can follow your hints with whatever folder the system or I have created; however, isn't it a waste of time? shouldn't have the installer done it that way firsthand?

I consider this question a no-nonsense one. Like other people here, I have inadvertently ruined a couple of systems just because I was a newbie then (more than I am now), and because user and data trees shared partition with system and boot trees. I agree with those who think having those trees in separate partitions helps you keep your system in good health.

---

### Post by oldfred on 2012-12-21
During install I have not ticked the correct options. Are you sure you chose /home, formatted ext4? 

You can post this to quickly see what is where:

sudo fdisk -lu
       sudo blkid -c /dev/null -o list
    
mount
        sudo cat /etc/fstab

---

