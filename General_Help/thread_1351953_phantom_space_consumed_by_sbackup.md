---
title: "phantom space consumed by sbackup"
date: 2009-12-11
forum: General Help
---

### Post by mortuk on 2009-12-11
Hey all

Wanted to do an overnight backup, and found an app called sbackup. I set it up, set it to copy certain folders over to my external hdd, pressed go and left it going

this morning my '/' drive ('/home' is on a different partition) is completely full, I run disk usage analyser and it cant seem to find where all the space is being taken up by. nothing has gone into the folder I specified to hold the backup

any ideas as apparently I have 0 bytes free now

---

### Post by callan79 on 2009-12-11
> **mortuk said:**
> this morning my '/' drive ('/home' is on a different partition) is completely full, I run disk usage analyser and it cant seem to find where all the space is being taken up by. nothing has gone into the folder I specified to hold the backup

any ideas as apparently I have 0 bytes free now


Hi,

I can't remember what sbackup's default folder is for storing backups, but I think it's /var/something.

I'm thinking that perhaps you changed the target folder and it didn't save properly for whatever reason.

So now you need to go into sbackup config and check it.

In order to find these backups, try this in terminal :

```

sudo find -name "*ful" -print
sudo find -name "*part" -print

```

Hope this helps!

Cheers
Callan

---

### Post by mortuk on 2009-12-11
Cool nice one. Found the file, deleted it.... still no space :(

I had to do a 'sudo nautilus' to actually find it, hit delete and its gone, but the space is still taken up. Nothing in trash as far as I can see

Any ideas?

---

### Post by mortuk on 2009-12-11
nevermind, found the files in /root/.local/share/Trash and got rid it there

cheers :)

---

