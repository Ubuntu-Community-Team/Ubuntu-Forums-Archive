---
title: "File system size"
date: 2005-03-16
forum: General Help
---

### Post by mat24 on 2005-03-16
Hello ,
Here's my problem ...

I had a small linux  / partition , and i wanted dto make it biger ...
so i used partimage to save the linux installation and qtparted (from rescue cd) to resiez the windows / linux partition ....

Everything succeeded but my  ubuntu don't take the changes , i mean  there 's aboiut 10 go on the ext3 partition  (about  8 go free)  and there's only the  same amount disponible that use to be  in the ubuntu  memory (about  3 go free).

How can i apply the changes ???

I tried fsck, e2fsck, it fixes some error but it'is not changing anything, i guess it should be a special file to edit ?? don't no... 

somebody to help me ???

---

### Post by bored2k on 2005-03-16
[QUOTE=mat24]Hello ,
Here's my problem ...

I had a small linux  / partition , and i wanted dto make it biger ...
so i used partimage to save the linux installation and qtparted (from rescue cd) to resiez the windows / linux partition ....

Everything succeeded but my  ubuntu don't take the changes , i mean  there 's aboiut 10 go on the ext3 partition  (about  8 go free)  and there's only the  same amount disponible that use to be  in the ubuntu  memory (about  3 go free).

How can i apply the changes ???

I tried fsck, e2fsck, it fixes some error but it'is not changing anything, i guess it should be a special file to edit ?? don't no... 

somebody to help me ???[/QUOTE]
 "disponible"? Are you hispanic?

wHat is it you want to do ?

Welcome btw.

---

### Post by mat24 on 2005-03-16
:roll: 

well french not hispanic .... 

I explain : i had a 5 go ext3 partition with ubuntu on it....
                 i used qtparted and partimage to resize (with rescue cd)
                  i restored my ubuntu image on the new partition (10 go)


Problems : ubuntu  still use my partition as a 5 go  partition !!!

I want the system to recognize my 10 go  partition ...

---

### Post by bored2k on 2005-03-16
[QUOTE=mat24]:roll: 

well french not hispanic .... 

I explain : i had a 5 go ext3 partition with ubuntu on it....
                 i used qtparted and partimage to resize (with rescue cd)
                  i restored my ubuntu image on the new partition (10 go)


Problems : ubuntu  still use my partition as a 5 go  partition !!!

I want the system to recognize my 10 go  partition ...[/QUOTE]
 french spanish italian les langues romantiques ;) .

That's quite weird problem ... I have not enough knowledge though, lets hope someone does sso we can all learn .

---

### Post by mat24 on 2005-03-16
langues romantiques  :p  ;)

thanx for your support  :lol:

---

### Post by az on 2005-03-16
You should have left the filesystem there after you made it bigger.  The filesystem (ext3) was grown for you.  When you restored the partimage image, you wrote back to disk the smaller filesystem.  You now have a lot of free space available.

just go back and resize the filesystem again with qtparted.

Partimage is great, but it just makes an exact copy.  Parted is great in that it can resize and move partitions without losing data.

---

### Post by mat24 on 2005-03-16
Okay i will try that !!!!
so if i understand ...
i go back to the system rescue cd ...
i use qt parted in order to modify again the partition ....
and it should be modify !!!
thanx

---

### Post by az on 2005-03-16
Yeah,  You do not have to make the partition any bigger - it already is resized  You just need to grow the filesystem on it.

---

### Post by mat24 on 2005-03-16
you grow the file system with qtparted ? thats it ?
how you define it ?

---

### Post by mat24 on 2005-03-17
OK i used 

resize2fs /dev/myhd
with the system rescue disk
and it works fine

---

