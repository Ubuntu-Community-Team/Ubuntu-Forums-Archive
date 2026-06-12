---
title: "Basic Permissions Question."
date: 2010-04-15
forum: General Help
---

### Post by Roasted on 2010-04-15
I was just screwing around with file permissions on my system and I came across something I wanted to address here. I set up a test environment to try and duplicate how I would drop a linux file server in a large environment, where certain users need different permissions for different folders, etc.

I came to find out that in order to open any type of file, whether it be a picture, text document, anything, all that user needs is READ permissions. But in order for that user to open a folder, "read" is not enough. They need read + execute.

Does my observation sound accurate? It seems as if read = good for all users to read any type of file, but read/execute is required in order for them to open a folder. Basically meaning if a user only has read on a folder, it's basically useless since they also need execute to even open the folder.

Am I correct on what I'm seeing?

---

### Post by Girya on 2010-04-15
Thats what I see. I skimmed man chmod and it seems that directories need x set for it to be readable. I wonder what the reason is for that. 

from man chmod:
> The  letters  rwxXst select file mode bits for the affected users: read (r), write (w), execute (or search for directories) (x), execute/search...


---

### Post by Roasted on 2010-04-15
Well, in my windows experience, read/execute always seem to go hand in hand from what I've SEEN, but I'm not the network admin who set up the permissions so that's only what I've seen and not what I've done. The only odd-ball seems to be write. Which would kind of make the windows way of permissions similar to how linux handles read/write/execute from regular files versus directories.

I GUESS in theory it makes sense. After all, you're browsing a directory when you open it, which is a "function" that I guess can be classified as executing it, whereas reading is simply opening what's already in the directory in front of you - aka any file that isn't a directory.

---

### Post by TitanusEramius on 2010-04-15
Yes, that is correct what you are saying.
Permissions for folders is slightly different than permissions for files. But one of the "features" in the system is that you can set folder-permissions in such a way that UserA can navigate through a folder without being able to see the content of that folder (regardless of what the file-permissions are). 


I tried to find some info on my claim, but my google-mojo must be low this morning since I failed :P

---

### Post by Roasted on 2010-04-15
New question, but I figured I'd throw it here since it's permissions related.

Let's say I have a directory, owned by administrator:share with 770 perms. 

I want 5 users to access the data in "share" and have read/write/execute permissions to it. These 5 users will be able to have full control over the data to do whatever they please to anything these 5 users create within that folder. As a result, those 5 users will be in the same group as I noted above: "share"

If I chmod -R 770 permissions, then that directory and everything inside is changed to 770 permissions. Okay, got it.

But what if Bob comes in tomorrow and adds a new file to that share? And then Greg comes in and adds some pictures? And Jen comes in and adds some openoffice documents? I want those files to indefinitely be "RWX" (7) permissions for the group. No matter what is created, no matter what happens, I want that folder and everything inside to be 770 permissions.

How can I do that? How can I rig up permissions on a directory so all files/folders are forced to take on 770 perms?

---

### Post by TitanusEramius on 2010-04-15
Since I don't (yet) have come around to actually test this myself, I can only point you in the right direction. I found this at [http://www.linuxforums.org/articles/file-permissions_94.html](http://www.linuxforums.org/articles/file-permissions_94.html) :
> 
If the SGID (Set Group Identification) attribute is set on a directory, files created in that directory inherit its group ownership. If the SGID is not set the file's group ownership corresponds to the user's default group. 
In order to set the SGID on a directory or to remove it, use the following commands:  
chmod g+s directory
chmod g-s directory  When set, the SGID attribute is represented by the letter "s" which replaces the "x" in the group permissions:  
ls -l directory
drwxrwsr-x  10 george administrators  4096 2006-03-10 12:50 directory

---

### Post by TitanusEramius on 2010-04-15
I was doing some reading in the forum and stumbled into this by Drenriza (it's the fourth down):[U]
[http://ubuntuforums.org/showthread.php?t=1453342](http://ubuntuforums.org/showthread.php?t=1453342)
[/U]

---

### Post by Roasted on 2010-04-15
Well, setting the GID sets the group - which is extremely helpful. But is there a way to set the permissions?  I guess I don't "need" it since setting the group is good, because as long as the group permissions aren't --- then we're in good shape. But I'm still curious if I can statically set the perms too...

---

