---
title: "Cant access folder because of Lucid upgrade problem"
date: 2010-05-02
forum: General Help
---

### Post by Adavur on 2010-05-02
Hello everyone.

Just upgraded to Lucid from Karmic, but I've got two problems:

[SIZE="3"]**1:**[/SIZE] After install I restarted, but it just showed the boot loader for 1 second and then black screen!

I then thought I would just reinstall Ubuntu so I used the Live CD to access the folders on the computer to get a backup.

[SIZE="3"]**2:**[/SIZE] But some of the folders in the Documents folder has got a white cross over it and when I try to open them I get the message: "The folder contents could not be displayed."

What I want is just to get the files (some of them is a bit important) and make a quick reinstall so if somebody knows a way to open the folders and make a backup it would be GREAT.

//Adavur

---

### Post by krismatth3 on 2010-05-02
Can you post the output of

```

ls -l ~/Documents

```

---

### Post by Adavur on 2010-05-03
Hello again and thanks for your reply.

The only way to access a terminal was by using the Live CD and this is my output:

```

ubuntu@ubuntu:~$ ls -l /media/.../Documents
total 588
drwx------  2 1000 1000   4096 2010-03-30 15:19 [COLOR="Blue"]Folder 1[/COLOR] *(not accessible)*
drwx------ 10 1000 1000   4096 2010-04-20 18:26 [COLOR="Blue"]Folder 2[/COLOR] *(not accessible)*
-rwxr-xr-x  1 1000 1000 553056 2010-03-25 19:55 [COLOR="YellowGreen"]file1.pdf[/COLOR]
drwxr-xr-x  2 1000 1000   4096 2010-04-07 19:55 [COLOR="Blue"]Folder 3[/COLOR] *(accessible)*
drwx------  2 1000 1000   4096 2010-03-30 15:22 [COLOR="Blue"]Folder 4[/COLOR] *(not accessible)*
-rwxr-xr-x  1 1000 1000  26624 2009-06-17 17:36 [COLOR="YellowGreen"]file2.doc[/COLOR]

```
(renamed files)

I also tried to access the files with the Puppy Linux Live CD, but it wouldn't even allow me to access the hard drive at all.

Thank you in advance.

---

### Post by Adavur on 2010-05-05
Anyone?

---

### Post by dino99 on 2010-05-05
as i understand, lucid is installed but you have issues at boot time, right ?
try to boot into recovery mode, if grub menu is hidden, at end of bios process, hold "shift" key down to show it, then select the 2d line (recovery mode) to boot

---

### Post by Adavur on 2010-05-05
Thank you man, I couldn't figure out how to show the GRUB menu. Booted into low graphic something and had access to my folders.

I still have no idea why I couldn't access some of the folders on the Live CD whilst I could access others, but thank you very much :)

---

### Post by dino99 on 2010-05-05
> **Adavur said:**
> Thank you man, I couldn't figure out how to show the GRUB menu. Booted into low graphic something and had access to my folders.

I still have no idea why I couldn't access some of the folders on the Live CD whilst I could access others, but thank you very much :)

nice :p

now into console:

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a
sudo dpkg-reconfigure gdm
sudo dpkg-reconfigure plymouth
sudo update-initramfs -u
sudo grub-mkconfig && update-grub

the easiest and secured way to access your files is to install MountManager and tweak it with your prefs for devices and partitions. Then for files: sudo chown "user" "the path to your file", where "user" is the user name you boot with.

---

### Post by StuartN on 2010-05-05
> **Adavur said:**
> ```

ubuntu@ubuntu:~$ ls -l /media/.../Documents
total 588
drwx------  2 1000 1000   4096 2010-03-30 15:19 [COLOR="Blue"]Folder 1[/COLOR] *(not accessible)*
```

The user id and group id (1000:1000) implies that it is not you, unless you run ls -ln to see id number instead of names.

**sudo chown -r user:usergroup path** will restore ownership (recursively).

---

