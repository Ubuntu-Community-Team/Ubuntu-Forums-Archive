---
title: "Trash and the ubuntu root user"
date: 2009-12-08
forum: General Help
---

### Post by sefs on 2009-12-08
I opened nautilus with sudo.  

I deleted a large file while in the nautilus launched as root.  Big mistake.  The space has not been recovered. 

It is not in the trash bin or in /home/user/.local/share/Trash

and I can not find a corresponding folder for the root user.

Where did that file go and why is it still taking up space if i have deleted it.

How can I recover this space as it is a very sizable bit of space.

Thanks.

---

### Post by wojox on 2009-12-08
Run these in the terminal:

```
rm -rf /home/*/.local/share/Trash/*/** &> /dev/null
```

```
sudo rm -rf /root/.local/share/Trash/*/** &> /dev/null
```

---

### Post by sefs on 2009-12-08
> **wojox said:**
> Run these in the terminal:

```
rm -rf /home/*/.local/share/Trash/*/** &> /dev/null
```

```
sudo rm -rf /root/.local/share/Trash/*/** &> /dev/null
```

What I am saying is there is no "/root/.local/share/Trash/*/**"

It  simply does not exist for the root user.

I have examined it via the terminal. 
And in nautilus when launched at root if i click on the trash folder I get this error

The folder contents could not be displayed.
Sorry, could not display all the contents of "trash": Operation not supported

Which is most likely because there is no /root/.local/share/Trash folder.

This has always been the case for me after a fresh install of ubuntu from the alternate CD.  It never bother me until now that I need to know where files go when i delete them in nautilus as root and there is no corresponding /root/.local/share/Trash

---

### Post by wojox on 2009-12-08
How exactly did you delete the file ? Shift+Delete, Right Click or just Delete ?

---

### Post by sefs on 2009-12-08
> **wojox said:**
> How exactly did you delete the file ? Shift+Delete, Right Click or just Delete ?

I had launched nautilus by going gksudo nautilus.

Then while in there I click on a file and deleted it from within natuilus by pressing the delete key.  It disappeared.

To exactly where I am not sure.

I've attached a file to tell the story of the no Trash folder for root.

---

### Post by Marlonsm on 2009-12-08
Use the disk space usage analyser, I think it's inside System > Administration. This way you can see where big files are, and maybe find that one.

---

### Post by sefs on 2009-12-08
> **Marlonsm said:**
> Use the disk space usage analyser, I think it's inside System > Administration. This way you can see where big files are, and maybe find that one.

I see Disk utility but no diskspace analyzer

---

### Post by John Bean on 2009-12-08
Assuming you know the file's name, why not just search for it... before deleting it properly this time ;-)

I'd use "find" from a terminal but a Nautilus search (as root of course) from the filesystem root (/) should find it.

---

### Post by cdenley on 2009-12-08
Try this, and post the output
```

lsb_release -id
sudo ls -AlR /root/.local/share/Trash
sudo touch aaa_delete_me
gksu nautilus $PWD

```
-delete the file "aaa_delete_me"
-close nautilus
```

sudo ls -AlR /root/.local/share/Trash

```

If the trash directory does not exist, it should be created by nautilus the first time you move something to trash.

---

### Post by sefs on 2009-12-08
> **John Bean said:**
> Assuming you know the file's name, why not just search for it... before deleting it properly this time ;-)

I'd use "find" from a terminal but a Nautilus search (as root of course) from the filesystem root (/) should find it.

I do not know weather to hug ya or buy you a beer (non-alcoholic) but you did it man!!!

In /home i have two folders...

/home/.Trash-root
/home/.Trash-0

I ran the find command as root from the root directory like you said and it turned that up.  And all the files are in there :)

This was a lesson well learned.

Thumbs up!

---

### Post by sefs on 2009-12-08
> **cdenley said:**
> Try this, and post the output
```

lsb_release -id
sudo ls -AlR /root/.local/share/Trash
sudo touch aaa_delete_me
gksu nautilus $PWD

```
-delete the file "aaa_delete_me"
-close nautilus
```

sudo ls -AlR /root/.local/share/Trash

```

If the trash directory does not exist, it should be created by nautilus the first time you move something to trash.

```

Distributor ID:	Ubuntu
Description:	Ubuntu 9.10

ls: cannot access /root/.local/share/Trash: No such file or directory

... created and deleted the file you said ...

ls: cannot access /root/.local/share/Trash: No such file or directory

```

Looked into /home/.Trash-0 and the file is in there not in /root/.local/share/Trash which does not exist of course.

---

### Post by Marlonsm on 2009-12-08
> **sefs said:**
> I see Disk utility but no diskspace analyzer

The problem is that I'm not running the default Ubuntu right now, I'm running Kubuntu, that is different. And I don't remember where it was, but I'm sure it is somewhere in the menus, maybe in Applications > Accessories...

---

### Post by cdenley on 2009-12-08
> **sefs said:**
> 
Looked into /home/.Trash-0 and the file is in there not in /root/.local/share/Trash which does not exist of course.

Nautilus is moving deleted files to the old location which was used a few releases back. Strange.

---

### Post by John Bean on 2009-12-08
Result :-)

Experience has told me to always use gksu rather than sudo to open nautilus (or any GUI app for that matter) to help avoid this sort of thing; sudo causes all sorts of confusion to desktop apps when a program needs to find some standard places like the home directory. That's how the trashed file ended up where it did.

Finally, don't delete anything from a root nautilus session without remembering to hold down the shift key before hitting the delete key.

---

