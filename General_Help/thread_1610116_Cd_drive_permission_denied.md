---
title: "Cd drive permission denied"
date: 2010-10-31
forum: General Help
---

### Post by Moose32315 on 2010-10-31
I can't seem to get ubuntu to allow me to access the cd drive.  It says permission is denied.  I've tried adding executable permission with chmod and unmounting and remounting the drive.  I also noticed that the owner of the drive is 501 even though that's not my user name.  I tried chown, but that didn't work either.  
 
I got those solutions above from a search, and I'm not sure what to try next.

This is the current ownership of files.

moose@Veritas:/media$ ls -l
total 2
lrwxrwxrwx 1 root root      6 2010-05-30 13:47 cdrom -> cdrom0
drwxr-xr-x 3  501 dialout 440 2010-05-24 23:56 cdrom0

---

### Post by Hippytaff on 2010-10-31
Does this happen when you try to access it via the terminal or when you click on the drive (or both)?

---

### Post by JKyleOKC on 2010-10-31
A user ID of 501 is typical for a RedHat, Fedora, or Mandriva system's first user, just like 1000 is typical for Ubuntu. Was the disk originally written from one of those systems?

If it was, the ownership and permissions were apparently made part of the disk at creation time, and since CDs are read-only, cannot be changed. You should, however, be able to read from it as any user, according to the directory listing you posted.

It may be possible to mount the disk manually with special options instead of the normal defaults. However someone else will have to spell these out for you step by step since I've not done it and would probably give you wrong information!

---

### Post by Moose32315 on 2010-10-31
I think it still says that when I try to access it from the terminal.  I've tried using wine to load it from the terminal and that didn't work; although, I may have been doing it incorrectly.  When I try to use wine from the terminal it says that it cannot find the file.  

I bought it and don't know who made the cd.  I thought that might be the reason for the different owner, but I though I should still be able to access it.  

I've actually just taken a look at cd again.  While I do have permission to access the files on the cd when go into it, it shows that the exe and main folder give no permissions to anybody but the owner.

---

### Post by Hippytaff on 2010-10-31
You should just have read permissions

---

### Post by Moose32315 on 2010-10-31
I may have found a solution.  I found somebody who had to remount the cd to reveal a number of hidden files.   Now I'm copying it to my computer so that I can change the permissions on it.  Hopefully it'll work.

---

### Post by Moose32315 on 2010-10-31
It worked.  Thanks for your input.

---

### Post by JKyleOKC on 2010-10-31
Where did you find the solution? Copying the URL to this thread may help others who have similar problems in the future...

---

