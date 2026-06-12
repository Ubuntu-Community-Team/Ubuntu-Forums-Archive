---
title: "Urgent !, corrupted usb thumb drive , wanted to recover and getting back the file"
date: 2010-07-17
forum: General Help
---

### Post by ubfu on 2010-07-17
I bought a 8 GB thumb drive last year but out of the sudden , not particular sure what causes it to get corrupted.
I cannot add files , delete them and some can't be open.But there are some can be open and view.It means it's half corrupted.

I wanted to recover back all those file and i found those GNU ddrescue and dd rescue 
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

But I dont know how to use on command line and i dont quite understand typing at terminal on ddrescue.

What's the different between GNU ddrescue and dd rescue .Besides those 2 which other good application for recovering corrupted usb files ?

Thank you , hoping for a quick help :)

---

### Post by ubfu on 2010-07-18
Any help guys ?

---

### Post by mike555 on 2010-07-18
if you can mount the usb ok , just copy and paste everything to your computer then try opening them ... just a thought ...

---

### Post by ubfu on 2010-07-19
I wanted to backup and recover most of them.Hard copy hoping to restore some of it.

---

### Post by etdsbastar on 2010-07-19
Can you open the drive. If yes then will u please tell me is there any lock sign coming in the files or folders, if yes then its permission problem if not then you can use scalpel to recover your files. 

Install it from synaptic and then type $ scalpel --help 

for instant help on how to use it.

---

### Post by ubfu on 2010-07-20
Yeh , I saw a lock sign at every file and folder , every of them.
What should I do ? 

When I "ls" to a text output I am getting an error .
```
ls: cannot access Medical: Input/output error
ls: cannot open directory ./Medical: Input/output error
ls: cannot access ./Files/File 31-2: Input/output error
ls: cannot open directory ./Files/File 31-2: Input/output error

```

Permission and files/folders are different which includes 
```
drwx------ 
d????????? 
-rwx------
drwxr-xr-x  9 root
-r-x------
dr-x------ 
```

Really confuse what should I do next ?
:(

---

### Post by rubylaser on 2010-07-20
I'd suggest using gddrescue (it's faster).
```
sudo apt-get install gddescue
```

You'll perform these actions on an unmounted disk.

ddrescue works in two passes.On the first pass, it grabs all the good sectors.
```
ddrescue -n /dev/old_disk /dev/new_disk rescued.log
```

The second pass grabs the error stuff, reading the info from the rescued.log
```
ddrescue -r 1 /dev/old_disk /dev/new_disk rescued.log
```

Finally, you'll need to do a filesystem check

Finally, you'll need to check your filesystem.
fsck -fyv /dev/new_disk

And, you should have as much data that could be recovered on the new drive.  As a note, the second part can take a long time.  Hope that helps.

---

### Post by ubfu on 2010-07-20
I dont understand the command 
"ddrescue -n /dev/old_disk /dev/new_disk rescued.log"

This 2 directory 
/dev/old_disk
/dev/new_disk

Which one is reading and output ? my usb thumb drive is at /media/disk
and to out the log to /media/disk-1
How should I enter ? 

ddrescue -n /media/disk /media/disk-1 rescued.log ?

---

### Post by ubfu on 2010-07-21
Problem solve by running 
sudo fsck -y /dev/sdc1

Thanks Jordan_U :)

---

