---
title: "linking a folder to a harddrive"
date: 2010-05-13
forum: General Help
---

### Post by yester64 on 2010-05-13
Hi,
i would like to link a folder, in my case that is 'Pictures' to a different harddrive with a folder containing pictures.
So whenever i save pictures it would save by default onto the harddrive with the linked folder.
How can i do that. I tried to do it with ls i think but this makes softlinks which did not let me open automatically open the other folder. omg i hope i don't make it to complicated to understand.

So here a visual plan of it.

the default folder
/
/home/user/pictures

like to link it to 

/media/pictures/photoshots
so this is the harddrive (another internal harddrive) which contains a different folder where i store my photos in general.

Any idea?

---

### Post by dv3500ea on 2010-05-13
You can mount the drive to /home/usr/pictures.
First find out what device the drive is:
Run System -> Administration -> System Monitor
click on the file systems tab.
Find the drive with directory /media/pictures/photoshots
Read what 'Device' it is eg /dev/sda2
Find out what type of file system it is under 'Type' (eg ext3)
Press alt-f2 and copy and paste this in:
```
gksudo cp /etc/fstab /etc/fstab-backup
```
Press alt-f2 again and copy and paste this in:
```
gksudo gedit /etc/fstab
```
Add a new line:
```
/dev/sda2 /home/user/pictures ext3 defaults
```
replacing /dev/sda2 with the device you found out and ext3 with the filesystem type you found out.
reboot.

---

### Post by bredman on 2010-05-13
Should be no problem

1. Make sure that /home/user/pictures does not exist. If it already exists, remove or rename it.

2. Use the terminal to enter the command
ln -s -T /media/pictures/photoshots /home/user/pictures

---

### Post by new_tolinux on 2010-05-13
> **bredman said:**
> Should be no problem

1. Make sure that /home/user/pictures does not exist. If it already exists, remove or rename it.

2. Use the terminal to enter the command
ln -s -T /media/pictures/photoshots /home/user/pictures
1. seems wrong. A folder has to exist before you can mount any drive to it according to what I know. You might want to be sure it's empty (at least there is nothing in it that you need while the drive is mounted there, because all existing files in that folder will be inaccessible).

2. [FONT=Courier New]sudo mount /dev/sda2 /home/user/pictures[/FONT] should also do the mounting part (replace /dev/sda2 according to dv3500ea's info), although it's not persistent so you'll lose it at least every time you reboot. Not the files you've written there, only that it's not re-mounted there by default (you can have it mounted there by default, as dv3500ean described).

---

### Post by bredman on 2010-05-13
There are 4 different formats of the ln command for different situations.

The -T version behaves as described above. Try it. 

I tested the command before posting. Did you test it before commenting?

---

### Post by new_tolinux on 2010-05-13
I have mounted an external drive manually to a specific folder for about six months every reboot. No I haven't actually re-tested the mount command again (I just recently fixed the /etc/fstab to do that for me).
But I do know (after using it five months of Jaunty and 1 with Karmic) that the command is correct (although /dev/sda2 is /dev/sdb1 in my case and /home/user/pictures was not the folder I used).

Maybe a folder shouldn't exist if you use ln, but for mount it definately have to exist.

---

### Post by oldfred on 2010-05-13
I have a /data partition that has all my folders for /home (original defaults plus others), one of those is Pictures.

For a new install I delete the current /pictures in home, and link in the data partition.

sudo mkdir /usr/local/fred/data
#Edit fstab first
# Entry for /dev/sdc6 :
UUID=a55e6335-616f-4b10-9923-e963559f2b05  /usr/local/fred/data    ext3         auto,users,rw,relatime               0  2  

in home directory I move before deleting:
mv Pictures oldPictures

# because I run this from my home the target is automatically /home
ln -s /usr/local/fred/data/Pictures

For each install I am not sure yet on the chown and chmod:
sudo chown -R fred:fred /usr/local/fred
sudo chmod -R 766 /usr/local/fred/data

---

### Post by alienprdkt on 2010-05-13
ln -s /home/user/pictures  /media/pictures/photoshots

that should work for creating what windows calls a shortcut.

---

### Post by yester64 on 2010-05-14
Hey guys, It did the job.
I did it with ls -s command and removed the folder before i was doing it.
Now i can place everything in puctures and it gets placed in the other harddrive.
Oh, btw. if i want to that for everyone on the computer, do i have to do it for every account? Haven't checked that so far.

---

### Post by KeyserSoze93 on 2010-05-14
Well, for existing account you'll have to do it manually. For new accounts, however, you can place a copy of your link in /etc/skel

---

