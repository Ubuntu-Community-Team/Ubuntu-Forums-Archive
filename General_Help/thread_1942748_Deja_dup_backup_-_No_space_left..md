---
title: "Deja dup backup - No space left."
date: 2012-03-18
forum: General Help
---

### Post by alpxp on 2012-03-18
Ok... Ricently I've decided to backup my /home/<USER>/ partition on the external HDD.
I have set up default Ubuntu 11.10 backup tool "Deja Dup" to backup: 
-every day 
-to external HDD 
-/home/<USER> (except Trash)
-with encription

It was fine for a week or so... It made first huge backup of whole home and did an incremental every day at night. Then it dicided to make a fresh full backup (for just in case, i guess) and it faild, says "No space left."
A little reseach have shown that there is "No space" in /tmp directory. So I have cleand /tmp and restart the backup -> faild again, I've cleaned the system as much as I can (now it has ~4.7 Gb free for /tmp) and tried again -> faild.

Also, I can't "Revert to previous version" any of the backed up folders for the same reason. Any of the actions with this backup ends up with "No space left."

I have ~400 Gb /home/<USER>
       1 Tb external HDD to backup to
       ~5 Gb free space in tmp

Ok, what do I do?

P.S. If It is the way it suppose to be (/tmp is the same size as backuped folder), then what is the correct way to backup huge "home" folders to external HDD?

---

### Post by alpxp on 2012-03-18
bump

---

### Post by darknuts on 2012-10-17
Wow. Its nice to see the people on the board are helpful. I'm having the same problem but I don't know how to fix it.

---

### Post by darknuts on 2012-10-17
Well I managed to fix it. It looks like the partition was not set up correctly and I only had a 500MB partition instead of a ITB. I went into the disk utility and changed the partition and DejaDup is backing up now. Thanks for your help everybody.

 :P

---

### Post by nicolasdiogo on 2012-11-28
same problem here

tmp has 2GB

target location is a SMB share with over 450GB FREE

but as soon as tmp is filled, it throws error of 'no space left' and stops.

it used work fine.

and now this.

does anyone have a solution for this?

thanks,

---

### Post by uhon on 2013-04-22
You can change the location of the tmp-Directory for deja-dub (duplicity-backend) as follows

Open a Terminal and type the following

```


TMPDIR=/othervolume/otherfolder
export TMPDIR
deja-dup-preferences
```

A option to configure this within deja-dup would be more convenient..

---

