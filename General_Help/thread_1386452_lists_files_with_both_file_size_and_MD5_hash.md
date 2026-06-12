---
title: "lists files with both file size and MD5 hash"
date: 2010-01-20
forum: General Help
---

### Post by jonathonblake on 2010-01-20
All:

Is there any utility that can provide a list of all files, and both the file size and md5 hash value. Preferably also including other hash values.

I've got 1.5 TB of files to go through, and delete duplicates..

Neither  fdupes or fslint are up to the task --- both claim files to be duplicates, when they definately are not. (Movies, and OOo documents are not identical, even if one is the script for the other, which in this case is not the case. Both fdupes and fslint claimed that those two files were identical. (And yes, I did look at them.))

jonathon

---

### Post by M1GEO on 2010-01-20
Here is a simple script I wrote to perform this function.  I added a couple of comments.  Feel free to chop it about to suit.

file:  hash_size.sh
```

#!/bin/bash

## Print column headers
echo "filename  md5hash filesize(KByte)"

## Create a loop in 'f' for all the files in the current dir
for f in *
do
        ## if 'f' is a regular file (not a device node or directory)
        if [ -f "$f" ]; then
                ## get 'f''s filesize
                filesize=`ls -la "$f" | awk '{print $5}'`
                ## compute 'f''s md5hash
                md5hash=`md5sum "$f" | awk '{print $1}'`
                ## print the filename, md5hash, and filesize
                echo "$f        $md5hash        $filesize"
        fi
done

```

Some sample output.  The printing isn't too great (justifying goes with filename length), but, it worked for me!
> 
filename	md5hash					filesize(KByte)
CIMG0011.JPG	bdfe7c092bd62e1d310cd0f56cb082b3	2198511
CIMG0012.JPG	577f00d12efe0788490bcf5677d179b9	2165156
CIMG0013.JPG	eb9c05b684a1ccbd270d7191cb4a2aea	2233466

(also the web-browser distorts formatting too)

Hope it helps.
Regards,

---

### Post by jonathonblake on 2010-01-25
> **Compu-king said:**
> Here is a simple script 

Thanks for the script.

Unfortunately, between the time I posted the question, and the time you responded, the drive in question failed.  :(

That means I've lost at least 1.x TB of data in the last 30 days. 
(Whenever I decide to backup the backup drives, the backup drives fail on me.) 

jonathon

---

### Post by J V on 2010-01-25
rsync ftw :P

---

### Post by M1GEO on 2010-01-26
Pants.  No-one likes failed drives :(

---

### Post by jonathonblake on 2010-05-10
> **jonathonblake said:**
> 
Unfortunately, between the time I posted the question, and the time you responded, the drive in question failed.  :(


Maybe it didn't fail. I can read it on my Linux box now.  (Electronic equipment has a habit of failing on me, then months later, working again.)

The script works, but it isn't practical for me, because of the sheer number of subdirectories - 25K.

I ended up using *Karen's Directory Printer* to print to disk everything on the drive, then using GREP to locate duplicate files by hash value.

jonathon

---

