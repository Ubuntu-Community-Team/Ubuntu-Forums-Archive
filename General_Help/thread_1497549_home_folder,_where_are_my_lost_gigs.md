---
title: "home folder, where are my lost gigs?"
date: 2010-05-30
forum: General Help
---

### Post by freacert on 2010-05-30
Hello

Unable to find an answer. Did an upgrade yesterday to 10.04. And all of a sudden my home directory appears to be full. Followed instructions of the great tutorial of how to recover lost disk space [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670) but no use at all. (great tutorial btw) and [https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

i ran auto-clean, auto-remove, no many big files of over 1G in home... 
just don know where my space is!!
properties of my home folder states it occupies 
>  34070 elementos, 3,7 GiB en total
(algunos contenidos son ilegibles) (some content is not readable translated) 

while i assigned over 47G to the home folder, files occupy according to gparted 36.37G, while my homefolder only contains 34066 elementos, 3,7 GiB en total.


erik@desktop:~$ sudo du -h --max-depth=1 /
[sudo] password for erik: 
293M    /lib
594M    /var
18M    /etc
4,5G    /usr
16K    /lost+found
4,0K    /selinux
4,0K    /old
8,0K    /mnt
160M    /opt
280K    /tmp
8,4M    /sbin
0    /sys
1,8M    /root
13M    /lib32
30M    /boot
7,9M    /bin
du: no se puede acceder a «/home/erik/.gvfs»: Permiso denegado
36G    /home
du: no se puede acceder a «/proc/15544/task/15544/fd/3»: No existe el fichero ó directorio
du: no se puede acceder a «/proc/15544/task/15544/fdinfo/3»: No existe el fichero ó directorio
du: no se puede acceder a «/proc/15544/fd/3»: No existe el fichero ó directorio
du: no se puede acceder a «/proc/15544/fdinfo/3»: No existe el fichero ó directorio
0    /proc
4,0K    /srv
468G    /media
16K    /.cache
14M    /dev
509G    /

---

### Post by sdennie on 2010-05-30
You could try:

```

find /home -type f -printf "%s %p\n" | sort -n

```

That will print the largest files in /home at the bottom of the list.  Though, based on the output you listed, it looks like you may have some things mounted in ~/.gvfs so, you may want to use -xdev to prevent it from traversing filesystems:

```

find /home -xdev -type f -printf "%s %p\n" | sort -n

```

Saludos

---

### Post by JustinR on 2010-05-30
Your hard drive partitions could be corrupt.

---

### Post by freacert on 2010-05-31
This morning all back to normal.. 


> **sdennie said:**
>  it looks like you may have some things mounted in ~/.gvfs 

I think the reason of the problem lies here. Ubuntuone or nepomuk trying to occupy a lot of space. Yesterday I was moving folders, emptying trash etc to free harddisk space while i saw the free space getting occupied again. Looked like a virus eating up hd....

Corrupted hd partitions: Thought about that, but couldn't figure out how to run the discutility as a root.  (too much too learn!)

---

### Post by Rasa1111 on 2010-05-31
> **freacert said:**
> This morning all back to normal.. 




I think the reason of the problem lies here. Ubuntuone or nepomuk trying to occupy a lot of space. Yesterday I was moving folders, emptying trash etc to free harddisk space while i saw the free space getting occupied again. Looked like a virus eating up hd....

Corrupted hd partitions: Thought about that, but couldn't figure out how to run the discutility as a root.  (too much too learn!)

allot to learn for sure~
but it looks like you are doing pretty good! :)

---

### Post by freacert on 2010-06-12
and now it is happening again. shutdown and restart doesnot help. And only 126 mB left in the homefolder...
anybody any clues where i should find the solution?

---

### Post by freacert on 2010-06-12
> **freacert said:**
> and now it is happening again. shutdown and restart doesnot help. And only 126 mB left in the homefolder...
anybody any clues where i should find the solution?

Now found a file, the 
/home/erik/.xsession-errors.old occupying 21.7 GB. 

can i call this a bug? How to prevent it from occupying so much space??

---

### Post by geirha on 2010-06-12
Oh, programs write log messages to that file (~/.xsession-errors). Something must be writing out a ton of them. Open it in an editor and see what type of messages are repeated alot.

---

### Post by freacert on 2010-06-12
> **geirha said:**
> Oh, programs write log messages to that file (~/.xsession-errors). Something must be writing out a ton of them. Open it in an editor and see what type of messages are repeated alot.

thanks, tried to open 21.7 gig in gedit, but as you can imagine...  so i deleted it, and have space again. I do have thoughts, but spare you all untill i experience the problem again..

---

### Post by geirha on 2010-06-12
Well, keep a close eye on ~/.xsession-errors then. If it grows beyond, say 100MiB, something is logging more than usual. You can output the last few lines with tail. ```
tail ~/.xsession-errors
```

Or tail it continuously with ```
tail -f ~/.xsession-errors
```

---

### Post by udaychaitanya on 2011-02-11
hellow, yesterday i have installed compiz and when it caused my firefox scrolling choppy i deleted it.then i tried to download a movie through transmission.it stopped there.after waiting for some time i killed transmission through terminal.then i tried to delete the movie file from homefolder.but i was unable to do that.so i tried to restart the system it said nautilus is working and i could not do so.even then i forced it.alas when i restarted, i lost some of my files from home folder.i dont have any partitions.i am new to ubuntu.please help me recover them                          regards

---

### Post by grahammechanical on 2011-02-11
Hi udaychaitanya

You are posting your problem on someone else's thread. Please do not do that. I, for one will not offer advice to more than one person at a time. You have a different problem. Please start your own thread.

In the meanwhile, do not create any files or delete any files or empty the waste basket. Click on the waste basket icon and see what is in there.

Regards.

---

