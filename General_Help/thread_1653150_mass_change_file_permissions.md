---
title: "mass change file permissions?"
date: 2010-12-26
forum: General Help
---

### Post by princeofnam on 2010-12-26
I recently backed up my home folder onto another HD. When I tried to transfer the files from the other HD back to the original HD after a fresh ubuntu install I noticed all my files were restricted to root access.  Even after moving the files back via root access I can still only access them that way.  Is there a way to mass change the permissions to all the files and folders within my original home folder?

---

### Post by mcduck on 2010-12-26
Sure.

```
sudo chown -R username:username /home/username
```

Be careful with that, though. you definielty don't want to accidenatlly chown any system file or directory, and a "chown -R in a wrong place would easily result in having to make a fresh install...)

.and the next time you make a backup, a nice trick is to do it into a .tar.gz archive. That will keep the ownerhip and permissions of files intact. Even if you move the archive to a FAT or NTFS drive...

---

### Post by MooPi on 2010-12-26
You can hurd all the files into one folder then chown the folder
```
mkdir bighurd
chown username -R bighurd
```
To avoid this same issue in the past I've copied files instead of moving the files.

---

### Post by princeofnam on 2010-12-26
So the file is on a separate harddrive.  before I do this I just want to make sure If i'm typing it right


> sudo chown -R sushi:sushi /media/13f3b05b-2691-4592-aa2b-ea10ba9ac8d9/sushi/

If i'm switching from root to sushi (my username) should it be "root:sushi?"

Furthermore if it's a folder with subfolders, files etc. will it chown everything or just the selected folder and immediate files within it?

---

### Post by coffeecat on 2010-12-26
> **princeofnam said:**
> If i'm switching from root to sushi (my username) should it be "root:sushi?"

No. The name before the colon is your username, that after the colon  your primary group. 

By the way, what is the filesystem on the separate (do you mean external?) drive?

---

### Post by princeofnam on 2010-12-26
both drives are ext4

---

### Post by princeofnam on 2010-12-26
does anyone know where chown will modify all folders and files within the selected directory though?

---

### Post by tredegar on 2010-12-26
> does anyone know *where chown will modify all folders and files within the selected directory though*?

*It modifies the file's attributes on the (linux) filesystem*.

**chown** can be used for one file: **sudo chown sushi:sushi /path/to/file**
Or it can operate recursively: **sudo chown -R sushi:sushi /path/to/dir**

Please double check your typing before you press return, or you can hose your system's file permissions.

This can only work on files that are stored on a linux filesystem ( ext2/3/4 etc ), but that seems to be your case.

Do you know how to use **man chown** ?

---

### Post by mcduck on 2010-12-26
> **princeofnam said:**
> does anyone know where chown will modify all folders and files within the selected directory though?

Yes, if you use the "-R" option.

---

### Post by princeofnam on 2010-12-26
no, what is man chown?

also, what resource did yall use to learn about linux and its terminal functions?

ps. thanks. chown worked like a dream

---

### Post by mcduck on 2010-12-26
"man" is used to view the manual pages for programs and commands. So, "man chown" would open the manual for "chown".

...and I learned everything simply by doing things. Figuring out what I want to do, and then reading the manuals, forum posts and if needed, searching with google to find out how to get those things done.

Actually I think spending lots of time on these forums, answering questions when I can and trying to find answers when I don't already know them, has helped a lot as well. That way you'll also learn from the answers other people give. And there's *always* somebody with a question you can help with, even if you have just started with Ubuntu and are still learning yourself. :)

---

