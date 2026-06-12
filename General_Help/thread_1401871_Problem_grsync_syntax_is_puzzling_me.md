---
title: "Problem: grsync syntax is puzzling me"
date: 2010-02-08
forum: General Help
---

### Post by fisheater on 2010-02-08
Hi,

Problem: grsync syntax is puzzling me

Detail: I get an error message when trying to grsync my NAS to an external USB HD for off site backup. My goal is to have new files updated every few months and keep this HD in another location:

```
rsync: opendir "/media/NAS_Storage/.systemfile" failed: Permission denied (13)
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1058) [sender=3.0.5]
```

This is how I have set up grsync with exclusions:

```
--exclude=".systemfile", --exclude="Nas_Prog", --exclude="BT"
```

My set up on grsync is: 
```
Preserve time, verbose, show transfer progress.
```

I thought I had understood the syntax of how to exclude a file/folder. Given this error message, I clearly dont have it right.

Suggestions?

Thanks 

FE

---

### Post by darolu on 2010-02-08
> Permission denied (13)
Check how permissions are set on your /media/NAS_storage unit, try running as root (or sudo); also review the options for this drive on your fstab file.

---

### Post by fisheater on 2010-02-08
Thanks for your reply, this stuff is well above my head! None-the-less I have been happy to roll up my sleeves and get under the hood of linux.

1.
After a bit of searching, I used this to see what my permissions are.

```
cat /etc/fstab
```

```
//x.x.x.x/NAS_storage    /media/NAS_storage        cifs    guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

But that makes me none the wiser. I had followed a how to mount a NAS from this forum and cut and pasted the above line, with some changes to make it work for my local setup. As you can see it has not p/w and I log in as guest. (I can hardly get no p/w setup to work, I couldn't add the additional variables of SSH, p/w, etc).

2. ```
sudo grsync
```
Oh my, how I like sudo. That ran the backup without any error messages. Perhaps I will need to use that as my standard method.

3. What is the option to make rsync mirror (I dont know what the term for this is) my HD? So that files that have been changed are updated, new files are added and files that no longer exist on the source are deleted from the destination?

UPDATE: ```
--delete (deletes files in destination which are not present in the source)
``` 
This looks like the command I was looking for, will try a simulation with grsync.

I will have a search and a read, will update this if I find any info.

Thanks again.

FE

---

