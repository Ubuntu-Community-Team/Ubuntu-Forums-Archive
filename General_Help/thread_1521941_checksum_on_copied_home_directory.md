---
title: "checksum on copied home directory"
date: 2010-07-01
forum: General Help
---

### Post by dimeotane on 2010-07-01
Can anyone tell my why my checksum failed after attempting to clone a directory?  Here's what I did:

I've tried to clone my /home directory using:

sudo rsync -aS /media/partition1/home/.     /media/partition2/home/.


Then to verify the copy was accurate I tried to do a checksum on the original and copied /home directory using: 

 sudo tar cvf  - home| md5sum

however they showed different checksums.

If I look at at the properties box in nautilus for each directory 
it tells me they have the same size (12.7GB) and number of files.

Any suggestions?:confused:

---

### Post by gzarkadas on 2010-07-01
Most applications store user settings (and some, such as firefox, other stuff too) inside the home directory. Most probably by the time you started to calc checksums, some of the processes that you had running have written something inside the home directory. Even a slight change will make an md5 sum different.

Use for each clone of your home this command, to create a list with md5sums for it (in /tmp, so that you do not create a new file in your home folder:

```

cd <~ or path of the clone>
find -type f -exec md5sum '{}' >> /tmp/<some-file-1|2> ';'

```Then use:
```
diff -U 0 /tmp/<some-file-1> /tmp/<some-file-2> | less
```to locate where the two clones differ.

---

### Post by dimeotane on 2010-07-02
Thanks gzarkadas for the thoughtful and detailed reply.   Some great tips there.

I should mention I was running my system from an external USB live Ubuntu install at the time I checked the other partitions.   So I'm not sure how/why the data could have changed on one.  Simply mounting it shouldn't have caused a change.

---

### Post by gzarkadas on 2010-07-03
If you rsynced while your source partition was mounted as /home (that is it was "live"), then the same argument applies. Only if you rsynced the partitions while both were not "live" it would be strange. 

Another possibility would be - just a though because I don't know the internals of tar - that the difference is introduced by tar (you calculated the md5sum of the tar archive, not of the files). If the order by which tar processes files is not guaranteed to be unique and deterministic, then the archive may have a different md5sum even if the files that contains do not.

In any case, only if you compare the individual md5sums can an answer be given.

---

