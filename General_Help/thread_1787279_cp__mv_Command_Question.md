---
title: "cp / mv Command Question"
date: 2011-06-20
forum: General Help
---

### Post by Curse on 2011-06-20
Would this command find all files that fit the guideline of "*.iso" and move them into the folder with their original names? If not, what would?

```

cp -r /media/Media1/Videos/*.iso /media/Media2/Videos/iso/*.iso

```

Trying to automate some file transfer :)

Or maybe....

find -r /media/Media1/Videos/*.iso > cp............. something like that?

---

### Post by nzjethro on 2011-06-20
AS far as I am aware, you don't need the second ***"*.iso"***.

I think

```
cp -r /media/Media1/Videos/*.iso /media/Media2/Videos/iso/
```

would do the trick, and copy all .iso files to /media/Media2/Videas/iso/, retaining the file names.

---

### Post by ruffEdgz on 2011-06-20
If you want to move them to a new locations:
```

mv /media/Media1/Videos/*.iso /media/Media2/Videos/iso/

```
If you wish to have two copies of the iso files, then use:
```

cp /media/Media1/Videos/*.iso /media/Media2/Videos/iso/

```

Cheers!

---

### Post by Curse on 2011-06-20
> **ruffEdgz said:**
> If you want to move them to a new locations:
```

mv /media/Media1/Videos/*.iso /media/Media2/Videos/iso/

```
If you wish to have two copies of the iso files, then use:
```

cp /media/Media1/Videos/*.iso /media/Media2/Videos/iso/

```

Cheers!

Excellent, one more question.

A lot of them are in subfolders in the first /Videos directory, how would I tell it to go into those folders as well to check for .isos?

---

### Post by nzjethro on 2011-06-20
Not sure how to get it to copy within subfolders, but check out [this.]("http://ubuntuforums.org/showthread.php?t=1385966")

---

### Post by v1ad on 2011-06-20
the problem with cp -r is it will only search the first directory for .iso and unless u have the folders named .iso it won't move further into folders searching. what we need here is a search then copy script if u want to copy or mv from the directories in. what u could do is.
ls -r /videos | grep some variables | cp *.iso . i'm sorry i can't write the whole script but it's been a while don't remember mos't of it.

---

### Post by Vaphell on 2011-06-21
if you need to do a full search in whole directory tree **find** command is your best bet - it is recursive and will look everywhere

```
find /media/Media1/Videos/ -iname '*.iso'
find /media/Media1/Videos/ -iname '*.iso' -exec mv -i "{}" /media/Media2/Videos/iso/ \;
```
first line does nothing but prints out iso files, 2nd line executes mv to /media/media2/vids/iso on each of matching files, {} is a placeholder for found filenames

---

### Post by dFlyer on 2011-06-21
> **Curse said:**
> Excellent, one more question.

A lot of them are in subfolders in the first /Videos directory, how would I tell it to go into those folders as well to check for .isos?

cp -r

---

### Post by lavinog on 2011-06-21
Something to think about with cp and mv:
If the goal is to move files and the source and destination are on the same partition, mv is a much quicker operation than copying and deleting the originals.
The reason for this is that the move operation just changes the inode data for the file, and does not actually move the file data.

Also, you should use the -v command too when doing operations like this, so you can see that the command is doing what you expect it should.

If you plan on copying a lot of large files, you might want to learn how to use rsync.  Rsync can give the transfer progress, along with resuming suspended transfers.

A common way that I use rsync is:
```

rsync -Pav *source dest*

```
the -P (capital) is for both --progress and --partial

---

### Post by v1ad on 2011-06-21
cp -r copies directories. use the find command as the fine gentleman has provided.

---

### Post by nothingspecial on 2011-06-21
You could just use

```
cp /media/Media1/Videos/*.iso  /media/Media1/Videos/*/*.iso /media/Media2/Videos/iso/
```

If the subdirectories are one deep, if they go deeper insert /* as needed

---

### Post by Curse on 2011-06-21
> **nothingspecial said:**
> You could just use

```
cp /media/Media1/Videos/*.iso  /media/Media1/Videos/*/*.iso /media/Media2/Videos/iso/
```

If the subdirectories are one deep, if they go deeper insert /* as needed

Would it work as 
```

cp /media/Media1/Videos/*/*.iso /media/Media2/Videos/

``` 
?

Why the first part? Wouldn't that look for files in the first directory, move them to the second then error on the third?

---

### Post by nothingspecial on 2011-06-21
> **Curse said:**
> Would it work as 
```

cp /media/Media1/Videos/*/*.iso /media/Media2/Videos/

``` 
?

Why the first part? Wouldn't that look for files in the first directory, move them to the second then error on the third?

cp moves whatever you tell it to to the last argument

so

```
cp blah blag
```

moves blah into blag, but

```
cp -r blah blag bananas
```

moves blah & blag into bananas

```
$ touch {1,2,3,4}.iso
$ mkdir a b blah
$ ls
1.iso  2.iso  3.iso  4.iso  a  b  blah
$ touch a/{d,e,f}.iso
$ ls a
d.iso  e.iso  f.iso
$ touch b/{x,y,z}.iso
$ ls b
x.iso  y.iso  z.iso
$ cp *.iso */*.iso blah
$ ls blah
1.iso  2.iso  3.iso  4.iso  d.iso  e.iso  f.iso  x.iso  y.iso  z.iso
```

---

### Post by Curse on 2011-06-21
> **Vaphell said:**
> if you need to do a full search in whole directory tree **find** command is your best bet - it is recursive and will look everywhere

```
find /media/Media1/Videos/ -iname '*.iso'
find /media/Media1/Videos/ -iname '*.iso' -exec mv -i "{}" /media/Media2/Videos/iso/ \;
```
first line does nothing but prints out iso files, 2nd line executes mv to /media/media2/vids/iso on each of matching files, {} is a placeholder for found filenames

This works perfectly, by the way!

Thank you all for the help and insight!

---

