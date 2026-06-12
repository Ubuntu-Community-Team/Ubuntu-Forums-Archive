---
title: "problem with rsync wildcard"
date: 2009-08-22
forum: General Help
---

### Post by PGScooter on 2009-08-22
hi, in the following code, the second * is expanded but the first is not. How can I get rsync to expand the first * ?

```
rsync -avv -b --backup-dir=/media/extdrive/bufor76*/budir2/ /home/jerome/ /media/extdrive/bufor76*/scotthome/ | tee /home/jerome/jtemp/rsynclog2.txt
```

I have read through the man page, and wildcards are discussed for various purposes, but I did not find anything directly useful to me. I though -s would help, but it did not do the trick.

any ideas?

thanks

---

### Post by PGScooter on 2009-08-22
bump

---

### Post by jordilin on 2009-08-22
I think the first is not expanded because is the value of a parameter, which in this case happens to be --backup-dir, and it accepts the '*' as it is, as if it belonged to the directory name itself. Actually, you don't need to provide the backup-dir parameter to have two places on sync with rsync.

---

### Post by PGScooter on 2009-08-22
> **jordilin said:**
> I think the first is not expanded because is the value of a parameter, which in this case happens to be --backup-dir, and it accepts the '*' as it is, as if it belonged to the directory name itself. Actually, you don't need to provide the backup-dir parameter to have two places on sync with rsync.

jordilin, thanks. I would still like to find out a way to have that backup-dir.

---

### Post by jordilin on 2009-08-23
> **PGScooter said:**
> jordilin, thanks. I would still like to find out a way to have that backup-dir.

Well, just took a look at man page and --backup-dir is receiver's end backup directory; so it can only be one and only one destination directory. That means, it cannot be expanded into different ones. If I were you, I would write a shell or perl or python script to handle the different options you want to achieve. I seem to understand that you want to backup "/home/jerome/ /media/extdrive/bufor76*/scotthome/" into different backup dirs?

---

### Post by PGScooter on 2009-08-23
> **jordilin said:**
> Well, just took a look at man page and --backup-dir is receiver's end backup directory; so it can only be one and only one destination directory. That means, it cannot be expanded into different ones. If I were you, I would write a shell or perl or python script to handle the different options you want to achieve. I seem to understand that you want to backup "/home/jerome/ /media/extdrive/bufor76*/scotthome/" into different backup dirs?

thanks for the reply jordilin. I see that I was unclear in my original post. Silly me-- of course you would think that with * I want multiple entries, but in fact the * would just match one directory. I would like to backup /home/jerome/ to /media/extdrive/bufor76.23AUG09/scotthome/, with rsync's "backup directory" (which accepts overwritten or deleted files from /media/extdrive/bufor76.23AUG09/scotthome/) as /media/extdrive/bufor76.23AUG09/budir2/  . "budir2" is a misnomer in this example. By "bu" I mean "backup of the original backup", if that makes sense.

I think that you are right-- I should do a small script. I was hoping, however, that there was a way to get bash to expand a path, even if rsync doesn't ask it to.

thanks

---

### Post by PGScooter on 2009-08-23
the following does the trick, but I would still like to see if there is a way for bash to expand a glob of a path more easily.

```

bubudir=/media/helpothers/bufor76*
echo $bubudir/budir2/
newbu=`echo $bubudir/budir2/`
rsync -avv --delete -b --backup-dir=$newbu /home/scott/ /media/helpothers/bufor76*/scotthome/ | tee /home/jerome/jtemp/rsynclog3.txt

```

---

