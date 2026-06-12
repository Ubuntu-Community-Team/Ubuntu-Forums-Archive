---
title: "Moving my files back, says have no permission"
date: 2010-06-19
forum: General Help
---

### Post by Kharlo on 2010-06-19
uhhm.... i dont knwo where to star..

from several problems with ubuntu/linux distros, just to have the compuer with main windows OS, Ubuntu as a second and backup and puppy too

after a week of madness codes sudos gedits. . . . installing reinstalling 2 3 may be 7 times....
the system is now quite stable (i had to erase the lucid lynx because nobody was able to help me with the problem of the missing panels. ill have to wait for a fix..

now i have a fresh install of 8.04 (i had to uninstall it because i move partitions ad grub wents down, i  tried EVERYTHING and nothing but reinstalling it)
i used puppy linux to extract my files (home folder) and save it int a new ext3 partition, then when this ubuntu8.04 was OK, i tried to move my files back. i tried to doit from ubuntu, and i saw a little padlock on the folder, i tryed to move it, and i cant, then i restart to tryit form puppy, i was able to doit from puppy, then i restart again back to ubuntu, now with the folder in ubuntu partition i now have to put each file/folder where it was supposed to be, but again i saw some older with the padlock icon and with the same problem, that i can't move it because i have no permision...

i tryed to find some help before opening this thread but all i want was to open a gksudo nautilus on terminal, but that doesnt fix anything, because that open a wibdows and i only can move "locked" files withing that folder, and those are my files i need to move it all the time, i can't open a gksudo nautilus every time i want to move one of my files


help please!

---

### Post by kevin.krenz on 2010-06-19
The files/folders are likely owned by the root account - check for this with the "ls -l" command at the terminal. It'll probably look something like this:

```
drwxr-xr-x  2 root  root      4096 2010-06-19 20:31 testDirectory
```

To change the owner to yourself, you can use the chown command:

```
chown user:group file
```

Where you make the appropriate substitutions for the user, group, and file (file can be a file or a directory). You can also use wildcards. For example, if I wanted to change everything in the current working directory to being owned by me, I would do this:

```
sudo chown kevin:kevin *
```

---

### Post by Kharlo on 2010-06-20
Hi!

that doesnt work
i wrote
sudo chown kharl:kharl *
and nothing happen, the directory continue locked

the super werid part of this is that i have reinstalled lot of time ubuntus distros and this is the first time, i did nothing different than others!

and why only THAT folder has those propierty? the only thing different of that folder is that i used puppy linux to copy from an old deffective ubuntu distro to a blank partition, then after a fresh ubuntu install im trying to move it back

help

---

### Post by kevin.krenz on 2010-06-22
Post of the output of "ls -l" while in the directory that contains the locked folders. Also, where is this directory?

---

### Post by Kharlo on 2010-07-03
Hi!
i have problem applying those commands and i need help because im needing those files
all seems too confusing

its just a folder named "backup" that i need back, i have files and more folders some locked some even  unacessible

please help

---

