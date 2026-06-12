---
title: "Need to take ownership/remove read only on a mounted HDD"
date: 2009-07-07
forum: General Help
---

### Post by interestinfellow on 2009-07-07
Alright, so I did the following [and mounted my hdd]("http://ubuntuforums.org/showthread.php?t=1182353").

Now I have acces to my drive, but can't write or modify any documents on it.  I need to badly.

I have since moved the mount point to a MyDocuments folder in my home folder (and edited fstab succesfully), and still have read only access.  

So I tried > sudo chown -R $user:$user /user/home/MyDocuments (my username is "user"... don't ask) and the files still belong to "root", and I still only have read only privilage.  

Someone please help, I don't really know what I'm doing (I love ubuntu soo much more that xubuntu, but my pc is a cruddy CeleronD 1.4).

Thanks!

---

### Post by akakingess on 2009-07-07
Have you tried the following?

```
sudo chown -hR $user:$user /user/home/MyDocuments
```
notice the 'h' in front of the R. Let's see if that gives you ownership.

---

### Post by synapsys on 2009-07-07
Where did the $ signs come from?

```
sudo chown -R user:user /user/home/MyDocuments                      
```

might have to manually unmount the drive first... take ownership of the folder... then re-mount.
Or simply change permissions so that everyone can read and write.

---

### Post by interestinfellow on 2009-07-08
The $ came from the instructions I found on a different thread, and bash processed all the files in the folder (thousands, took about 7 min).

I have sudo thunar 'd and right clicked, the owner is root on the mount folder, and subfolders/files.  The permission for all users is read/write.

I'm going to try the h switch with no $ now.  BRB.

(((10 min later)))

Nope.  I ran the script, and then tried to copy a file and paste it.... no go.

i typed 
> sudo chown -hR user:user /home/user/MyDocuments
and it processed everything.  But It's still owned by root, and I have read only access.

Please help (more)

---

### Post by rbc on 2009-07-08
Just out of curiosity, what's the fstab entry look like, and how did you create the MyDocuments directory under /home/user?

---

### Post by synapsys on 2009-07-08
> **synapsys said:**
> might have to manually unmount the drive first... take ownership of the folder... then re-mount.

Did you try unmounting it first?

```
sudo umount /dev/sd??
```

---

### Post by interestinfellow on 2009-07-08
> /dev/sdb1 /home/user/MyDocuments/ ntfs ro,user,auto,noexec,umask=0 0 0 and i'll unmount it and chown it now.

---

### Post by interestinfellow on 2009-07-08
Well damn it Synapsis, you just go right ahead and get yourself a cookie... and a sundae while your at it!

Worked like a charm.  Thanks for all the help, all of you.

EDIT:
Just a cookie.  I have to do it every time I boot.  %$#@ Xubuntu.... I'm loading Ubunut 9.

---

### Post by synapsys on 2009-07-09
I may be too late... but try this one more thing.

Install ntfs-3g (if it's not already installed)

With the 'MyDocuments' partition mounted open terminal and type:

```
blkid
```

Find the UUID for sdb1

Edit fstab one more time (yes i know)
Change line to this:

> UUID=009C76F79C76E716 /home/user/MyDocuments ntfs-3g defaults,locale=en_US.UTF-8 0 0

(of course substituting your own UUID)

---

