---
title: "rsync - to exlcude files lasting with ~"
date: 2009-08-20
forum: General Help
---

### Post by terrylai on 2009-08-20
Dear all,

I used rsync to backup my home user data to another hard disk.

However, I found that the file lasting with ~ (e.g. file.ext~ and file~) are also copied but cannot be excluded.

Do anyone know how to exclude them ?
BR,
Terry:KS

---

### Post by DaithiF on 2009-08-20
Hi,
include this option?  works for me.
 --exclude='*~'

---

### Post by tgeer43 on 2009-08-20
Sure, I've never actually done this but you can use wildcards with the --exclude command line option.

So to exclude all files with a ~ suffix you could use these two options on your rsync command line:

--exclude='*.*~'  and  --exclude='*~' (don't forget to include the single quotes)

See 'man rsync' for details or google 'rsync exclude file types'.

tgeer

---

### Post by terrylai on 2009-08-20
Actually my command is:

rsync -avz --delete --exclude-from=/home/aaa/.rsync/exclude.txt /home /media/disk-2 

and after viewing your replies I had modified the exclude.txt and added the last 2 lines:

/home/aaa/.cache
/home/aaa/.local/share/Trash
/home/aaa/.mozilla/firefox/4043v93n.default/Cache
/var/cache
'*~'
'*.*~'

However, the files lasting with ~ still be copied.

:confused:

---

### Post by tgeer43 on 2009-08-20
Since you are using an exclude file rather than specifying on the command line then the single quotes may not be needed.

All of your other excludes specify the exact file and path but when using wildcards where the files may be located anywhere, you may need to use the -r option so they will be searched for and excluded recursively. I'm going from memory here so again, try 'man rsync' or google 'rsync exclude file types' to get the full scoop.

tgeer

---

### Post by garryknight on 2009-08-20
Try moving the two new lines to the top of the file.

---

### Post by tgeer43 on 2009-08-20
> **garryknight said:**
> Try moving the two new lines to the top of the file.Now you've got my curiosity piqued. What effect will moving them to the top of the list have?

Inquiring minds want to know.

tgeer

---

### Post by DaithiF on 2009-08-20
Hi,
as mentioned previously, remove the quotes if using an exclude-from file (since you don't need to protect the patterns from shell expansion if rsync is reading them from a file).

Also, I don't think you need both patterns: *.*~, *~
*~ should be enough as the . character isn't special so *~ should match a file like somefile.txt~ just fine.

---

