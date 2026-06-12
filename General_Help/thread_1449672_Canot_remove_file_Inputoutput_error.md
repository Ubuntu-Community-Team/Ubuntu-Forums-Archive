---
title: "Canot remove file Input/output error"
date: 2010-04-08
forum: General Help
---

### Post by brain!ac on 2010-04-08
Hi
I got a new HDD like a Storage on my Ubuntu ,it is formated as ext3 and i am able to mount it ,but sometimes while downloading from FTP ,when the session broke Ubuntu crates some ./afternature.mp4 Input/output error ,which i can see on "ls  -l" ,and that causes great troubles to me ,because i can not copy or write on that disk another file with the same one which is created like this ,these error are gone only if i format the hdd .

My mounting command is "mount /dev/hdb3 /tmp/hd ext3 rw 0 0"
So is that possible to remove these error without formatting the disk .

PS:I did a lot of search for that error ,on unix forums also here but i didn`t find a concrete answer ,i found a thread which is for that case but removing with inode is impossible because on ls -l i`m not receiving the inode  .

Best on advance

---

### Post by deracled on 2010-04-08
You can try removing the files using their* inode* number and find

do an **ls -i ** first to get their inode numbers (*inum*) and then use* find* to delete them 

here's an example:
I created a file with  **touch "bad&file"**
**-rw-r--r--  1 user user            0 2010-04-08 12:29 bad&file**

"ls -i" will show it's inode number:
  2425095 bad&file     

and then use find to list it (verify first) 

[B]$find . -inum 2425095
./bad&file[/B]

and now delete it, again using find:

**find . -inum 2425095 -exec rm -f {} \;**


Hope this helps 
Doros

---

### Post by brain!ac on 2010-04-08
Thanks for reply but ls -i is displaying only good files which are healthy .

so it gives me a list like that 

```

ls: ./afternature.mp4 : Input/output error
ls: ./afternature1.mp4 : Input/output error
376837 file1

```

---

### Post by brain!ac on 2010-04-13
Any help yet ?

---

### Post by bolucpap on 2010-04-13
Shouldn't brainiac run unmount and run a fsck anyway to ensure his filesystem is healthy? That should also take care of the corrupt files too IMO. 
Brainiac, I am no expert of fsck, so I wouldn't advise on doing that until there is some confirmation from more experienced guys that it is ok to do.

---

### Post by brain!ac on 2010-04-15
Well i solved that case ,but on a not logic way .

I tried to delete that partition and make a new one ,using **fdisk** .

First i used 

```

fdisk /dev/hda 
p #to print parition list

d #to delete a partition
3 #number of the partition

p #to verify if that partition was deleted

n #to create a new parition
p #for primary partition not extended one
3 #number of that partition
136 #which fdisk sugested first block and so i did
1398 #the last block which fdisk sugested or it used it by deffault


```

So who has a issue like that ,it is not the best choice but it worked out .

---

