---
title: "aMule not completing files"
date: 2010-03-13
forum: General Help
---

### Post by tali_le on 2010-03-13
says it's permission denied to create a file in the incoming directory

i run amule 2.2.6 on ubuntu 9.10

i don't know what the issue is but from amule forums they say i need to change my ubuntu settings so i came here as well...

tali

---

### Post by kvarley on 2010-03-13
Can you get at the preferences within aMule? You need to make sure you have **read and write** permissions to the download directory.

---

### Post by tali_le on 2010-03-13
my incoming directory is /home/talile/.aMule/incoming

i should have a regular permission for that?
how do i check this?

tali

---

### Post by Enigmapond on 2010-03-13
Right-click/properties/permissions.

---

### Post by tali_le on 2010-03-13
i looked into the permissions

i have create and delete files - in the folder access
and a --------  - in the file access

is that good?

i tried changing it to read and write but couldn't save it

tali

---

### Post by rnerwein on 2010-03-13
hi
open a terminal and execute the following commands:
ls -ld /home/talile/.aMule/incoming
ls -ld /home/talile/.aMule
ls -ld /home/talile
all the output should be: drwxr-xr-x talile talile .......
if not you have to change the owner by using sudo:
sudo chown talile:talile /home/talile/.aMule/incoming
sudo chown talile:talile  /home/talile/.aMule
and chmod 755  /home/talile/.aMule/incoming
chmod 755  /home/talile/.aMule

i think that's it
ciao

---

### Post by tali_le on 2010-03-13
talile@talile-laptop:~$ ls -ld /home/talile/.aMule/Incoming
drwxrwxrwx 2 talile talile 4096 2010-03-13 18:33 /home/talile/.aMule/Incoming
talile@talile-laptop:~$ ls -ld /home/talile/.aMule/
drwxr-xr-x 4 talile talile 4096 2010-03-14 05:46 /home/talile/.aMule/
talile@talile-laptop:~$ ls -ld /home/talile/
drwxr-xr-x 34 talile talile 4096 2010-03-13 20:23 /home/talile/
talile@talile-laptop:~$ sudo chown talile:talile /home/talile/.aMule/Incoming
[sudo] password for talile: 
talile@talile-laptop:~$ sudo chown talile:talile /home/talile/.aMule/
talile@talile-laptop:~$ chmod 755 /home/talile/.aMule/Incoming
talile@talile-laptop:~$ chmod 755 /home/talile/.aMule/

i did this, restarted my amule and still it dosen't work
i've got clue what the prob is

tali

---

### Post by carandraug on 2010-03-13
The only thing I can think at the moment is if amule is running as another user. Try this command

```
ps aux | grep amule
```

this should the list of processes that have amule on its name. Two should at least come out, the process "grep amule" which is the one that you just ran looking for amule and amule itself. Other things that can come out is for example firefox if opened it by clicking on a link with amule on it.

Once you identify the line that corresponds to the amule process check the first number of that line (the user id that's running the process) and run the following command to find it's username (of course you must replace UID by that number). If it's not yours, there's the problem.

```
getent passwd UID

```

I'll exemplify shwoing the output while looking for firefox instead of amule (I don't have amule installed)

```
carandraug@holy-symbol:~$ ps aux | grep firefox
1000       572  0.0  0.0   3040   792 pts/3    S+   23:31   0:00 grep --color=auto firefox
1000     27437 15.7 15.0 389684 153476 ?       Sl   20:14  30:58 /usr/lib/firefox-3.5.8/firefox http://en.wikipedia.org/wiki/Serendipity
carandraug@holy-symbol:~$ getent passwd 1000
carandraug:x:1000:1000:Carnë Draug,,,:/home/carandraug:/bin/bash
```

By looking at the output of the last command I see that it's the user carandraug (the first word of the output) that started that process. In your case, if this is different than talile, that's a problem.

---

### Post by tali_le on 2010-03-14
hi

first, thanks for all the help

but the prob isn't solved

any more ideas?
i'm getting desperate?

tali

---

### Post by Enigmapond on 2010-03-14
Well I never had a problem with Amule...it creates the folder .amule and then what's being downloaded are in .amule/temp and then it moves the completed to .amule/incoming. Perhaps change the finished folder to a custom one and just change the folder locations in the amule preferences.

---

