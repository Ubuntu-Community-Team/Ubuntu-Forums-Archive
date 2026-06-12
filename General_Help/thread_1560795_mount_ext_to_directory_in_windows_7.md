---
title: "mount ext to directory in windows 7?"
date: 2010-08-25
forum: General Help
---

### Post by iarenoob on 2010-08-25
Ok, so I know that it is possible to mount ext filesystems from windows using either extfsd or extIFS drivers.  What I want to do is, after mounting it to a drive letter with the driver, to further mount it to, for example, the "my documents" directory.  The thing is, disk management in windows 7 won't recognize the ext partition so it won't let me mount.  Is there any way to do this?

---

### Post by Mark Phelps on 2010-08-25
Unless they recently updated the ext filesystem windows driver to now handle Ext4 filesystems, the answer is NO.  You can't mount a filesystem in MS Windows that it doesn't understand.

Besides, this is the "Ubuntu forums". If you have Windows 7 questions, you should also consider posting them to the Windows 7 forum -- sevenforums.com.

---

### Post by iarenoob on 2010-08-25
my question isn't whether it can handle the filesystem or not, and im actually not using ext4. My question is, assuming that the driver can handle it, can I then mount it to a directory
 
Just to clariy, windows DOES understand the partition...sort of, it is mounted as a drive letter and i can access it with windows explorer.  The problem is that disk management, the thing that does the mounting, doesn't recognize it.

---

### Post by iarenoob on 2010-08-26
Ok this is solved....sort of.  A symbolic link can be used in place of a mounted directory to point to the ext partition.  
However, my reason for doing this was to put my windows data (my users\myname folder) into the new partition.  Windows apparently really hates ext and will become incredibly unstable, when I did this my comp spontaneously blacked out and rebooted itself about 3 minutes after logging in fine.
So you can create a symbolic link that will act identical to a mount point but using it as your user folder like I did will cause problems.

And in response to the previous post, I didn't use the windows 7 forums because Im guessing very few ppl there have reason to care/know about any filesystems ext2 and above.

How do I mark something as solved?

---

