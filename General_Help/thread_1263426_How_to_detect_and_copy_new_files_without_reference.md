---
title: "How to detect and copy new files without reference to destination"
date: 2009-09-11
forum: General Help
---

### Post by Snowman314 on 2009-09-11
I'm trying to set up a system where the server on my lan periodically checks the shared music folders on the other machines, and when it sees files that weren't there previously, it copies them to a temporary folder on the server.
 I cant just synchronise the folders, as the temporary folder has its contents altered/moved/deleted shortly afterwards.
 What I'm going for is a script that will run cp on those files identified as not being there last time, but can anyone help me with a way of finding them in the first place?

I'm assuming that the network folders will be mounted to known locations, and that the source folders wont be altered beyond the addition of new files.

I've searched for this but not found anything. Apologies if this has been covered.
Thanks in advance.

---

### Post by akakingess on 2009-09-11
I am not an expert on bash scripting (as a matter of fact I have just started to read up to learn), but you may want to start by checking out all the commands and options available within bash when it comes to the copy (cp) command.

---

### Post by Snowman314 on 2009-09-11
> **akakingess said:**
> ...you may want to start by checking out all the commands and options available within bash when it comes to the copy (cp) command.

As far as I can tell, the only option is -u, which only copies files if they are new or don't exist in the destination folder. My problem is that they never will exist in the destination folder. 
 I need a copy that will remember what was in the source folder the last time it was run.

---

### Post by amac777 on 2009-09-11
In the NTFS file system, there is an attribute for each file called the "archive bit". This bit indicates whether the file has been backed up previously. If the MP3 files you want to backup are stored on NTFS shared drives, and there is no other backup software that is already utilizing the archive bit for its own purposes, you could use this bit to indicate which files you've already copied. Copy only the files with the archive bits set to a 1 (this is how the file will be when a user first puts it there), and then clear the archive bit when you copy the files so it won't get copied the next time.

Ext3 doesn't have this attribute, but it does have a "modification time" (mtime) associated with each file, so you could probably use the mtime for each file to know which ones were added to the shared directory since the last time you scanned for new files. The only problem is you will have to confirm that when users put the files there to begin with that the mtime is getting set to the current time. I think it depends on how they copied the file whether or not the mtime will get set to the current time or stay preserved at the original time

Those are the two easiest ways I can think of to do it but without knowing what kind of file system(s) you are working with it's hard to know if either of those will work for your purposes.

---

### Post by Snowman314 on 2009-09-11
> **amac777 said:**
> Those are the two easiest ways I can think of to do it but without knowing what kind of file system(s) you are working with it's hard to know if either of those will work for your purposes.

Thanks for those ideas. Good point regarding the filesystems. The shared folders are a mix of NTFS and ext3. So I'll sit down and try out what you suggested. 
 I was hoping for something along the lines of comparing the list of file paths with a previous copy, but running diff will consider every line after a difference to also be different, even though the lines are just offset. The attractiveness of this method would be that its pretty much independent of file systems etc, or at least as far as I can think of.

---

### Post by akakingess on 2009-09-11
> **Snowman314 said:**
> As far as I can tell, the only option is -u, which only copies files if they are new or don't exist in the destination folder. My problem is that they never will exist in the destination folder. 
 I need a copy that will remember what was in the source folder the last time it was run.

My apologies, I completely disregarded the fact about the "temporary folder" and that the files would be moved from there shortly thereafter.  That may be a tough nut to crack and I wish you the best of luck with it, would there be a way to keep a shortcut or alias in the temp folder as a reference point? Beyond that, I will probably be of no help.  Good luck to you on this project.

---

