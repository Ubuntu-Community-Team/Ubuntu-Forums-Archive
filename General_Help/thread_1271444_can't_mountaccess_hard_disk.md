---
title: "can't mount/access hard disk"
date: 2009-09-20
forum: General Help
---

### Post by Grimtooth on 2009-09-20
Hi, i'm actually new to this things so i need help. any help is greatly appreciated.

well to start off, i can't access any of the partitions in my hard disk except for the filesystem partition. it says 'Could not mount <partitionname> Authentication is required'. before i updated this laptop, it asks me for the password and it bugged me. So i searched through and some said try updating the laptop.. it didnt help me.

I'm using karmic btw.

---

### Post by Peacefulpieofdeath on 2009-09-20
[http://wiki.eeeuser.com/howto:sd_permissions](http://wiki.eeeuser.com/howto:sd_permissions)

I think i used this to fix it, the ubuntu part

Edit: 
sudo chown -R yourname:yourname /dev/(partition name like sda1)
sudo chmod -R 755 /dev/(partition name like sda1)

---

### Post by Grimtooth on 2009-09-20
i followed up till the one it says to type in 'ls -l' this is what i got

total 4
lrwxrwxrwx 1 root root    6 2009-09-12 19:34 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2009-09-12 19:34 cdrom0

so... which one is my filesystem and which are the rest?
sorry for the stupid questions i may ask.. i just started using a fews days ago.

---

### Post by Peacefulpieofdeath on 2009-09-20
Make sure the ones you want are mounted...

then take the ones that say root root and replace them in the <disk name> part

hope that helps

---

### Post by Grimtooth on 2009-09-20
i tried to mount but it says authentication required. i have 4 partitions and from the output above i can only see 2.. i think.

---

### Post by Peacefulpieofdeath on 2009-09-20
Try going to system -> admin -> authorizations -> storage -> mount file systems from internal drives. 

Also autentication is your password no? When you try mounting them does a screen pop up asking for your password?

---

### Post by Grimtooth on 2009-09-20
well.. when i tried to mount it a pop up box appeared without asking for password.

---

### Post by Peacefulpieofdeath on 2009-09-20
Ok look in gnome partition (if you dont have it sudo apt-get install gparted) and give me the /dev/sda(what) of the 2 partition you are trying to mount.


Also if you have msn add me, it would go faster

[email]Peacefulpieofdeath@hotmail.com[/email]

---

### Post by Grimtooth on 2009-09-20
its /dev/sda1 with ext2, and /dev/sda2 and /dev/sda5 with ntfs filesystem

---

### Post by Peacefulpieofdeath on 2009-09-20
Try sudo mount 

> sudo mount /dev/sda1
sudo mount /dev/sda2
sudo mount /dev/sda5

if that does not work try
> 
cd /
cd media
sudo mkdir disk1
sudo mount /dev/sda1 /media/disk1


If that worked

> 
cd /
cd media
sudo mkdir disk3
sudo mount /dev/sda5 /media/disk3

cd /
cd media
sudo mkdir disk2
sudo mount /dev/sda2 /media/disk2


Tell me if that worked.

---

### Post by Grimtooth on 2009-09-20
it works for the moment. i tried restarting and unless i retype 

sudo mount /dev/sda1 /media/disk1
sudo mount /dev/sda2 /media/disk2
and
sudo mount /dev/sda5 /media/disk5

it wont let me access those partitions.

---

### Post by Peacefulpieofdeath on 2009-09-20
Ok it did what i wanted it to, now lets make it do it every time w/o those anoying comands.


First in you other message you said sudo mount /dev/sda5 /media/disk_***5***_ i made you point it at disk3, if you made it w/ disk5 make sure you change the commands you put in fstab.

> 

sudo gedit /etc/fstab


Add the lines


/dev/sda1       /media/disk1     ext2    nodev,nosuid        0       2
/dev/sda2 /media/disk2 ntfs nodev,nosuid        0       2
/dev/sda5 /media/disk3 ntfs nodev,nosuid        0       2

Save and close.



If the 2 ntfs partition mount after trying that, just change in the fstab the words ntfs for fuseblk.

---

### Post by Grimtooth on 2009-09-20
it works! thanks a lot man!

---

### Post by Peacefulpieofdeath on 2009-09-21
No problem, any time.

---

