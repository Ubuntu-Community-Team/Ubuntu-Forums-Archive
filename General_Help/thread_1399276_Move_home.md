---
title: "Move /home"
date: 2010-02-05
forum: General Help
---

### Post by AmbiguousOutlier on 2010-02-05
I partitioned my drive, which xbmc live (ubuntu mobile) is installed on (sdc1) and mounted /home on the second partition (sdc2), I now want to dual boot on the second partition. I'm thinking if I overwrite my /home folder then xbmc wont work anymore. 

Is there a way to move /home to my first partition. There is currently nothing in there all data gets saved on separate disks. 

Also can I partition sdc2 to become sdc2 and sdc3 then I install ubuntu 9.10 on sdc2. Will my xbmc live installation still be intact on sda1?


Thanks for any help.

---

### Post by AmbiguousOutlier on 2010-02-05
Wont boot please help!!!

I figured I would just change /etc/fstab so I added this line;

/dev/sdc1 /home ext4 nodev,nosuid 0 2

now it asks me to log in and says;

```
No directory, logging in with HOME=/ 
```

However I can type cd /home and it takes me there?

What do I do?

---

### Post by Richard1979 on 2010-02-05
> **RhysGM said:**
> Wont boot please help!!!

I figured I would just change /etc/fstab so I added this line;

/dev/sdc1 /home ext4 nodev,nosuid 0 2

now it asks me to log in and says;

```
No directory, logging in with HOME=/ 
```However I can type cd /home and it takes me there?

What do I do?

I would guess from the error message that /home is really /

---

### Post by gmargo on 2010-02-05
> **Richard1979 said:**
> I would guess from the error message that /home is really /

Not quite.  That is the message you get if you log in successfully (i.e. entered the correct password) but the home directory specified in the /etc/passwd file does not exist.  The system still lets you in, but puts you in the root directory.

---

### Post by AmbiguousOutlier on 2010-02-05
No need to worry about this anymore I tried a complete re-install

---

