---
title: "Permissions:  Allow write, deny delete"
date: 2011-06-01
forum: General Help
---

### Post by emptythevoid on 2011-06-01
Is there no good way to assign permissions so that users can create files, modify files but cannot delete them?  I know there's the sticky bit, but all that does is say that only the owner (who is a single user) is able to delete them.  Ideally, what I want is to be able to use the sticky bit, but apply it to the file's group, rather than the file's owner.  

Here's the example:  I have a folder that is shared publicly.  I want people not belonging to the folder's group to be able to create files, modify files, but not delete them.  I want the folder's group to have full control.  This would be possible if the sticky could apply to the folder's group, instead of the owner.

I've looked into ACLs, but from what I gather, it's still just assigning permissions "none" "read" and "write," none of which would stop someone deleting a file, while still letting them create or modify (unless they were the owner, which is not helpful).   

Any thoughts would be appreciated, even if they confirm that I'm out of luck.

---

### Post by baarn on 2011-06-01
i am not sure if thats possible, although deleting a file just kicks out an index entry on your filesystem, and modifiing a file actually writes stuff to the file...
even if it was possible, it would still be possible to open the file and delete all of its content.  

how about some kind of subversion or something like that? i dont know about what kind of files you are talking here, subversion can get nasty if you want to store big files, but maybe that would be a solution... atleast for smaller files.

---

### Post by emptythevoid on 2011-06-01
This is on an Ubuntu samba file share for our work.  It stores your basic office essentials - things like Word files, spreadsheets, PDFs, etc.  The share has a very large directory structure, and I use permissions on different bits of the structure depending on who needs what.  We rely heavily on groups to determine who can access what.  It's currently running about 200GB or so of data.

Except for me, everyone is accessing this share using Windows.  My managers want to create a folder where non-privileged users would be able to create Word files, and/or modify existing Word files (and other misc filetypes).  These files would be viewable to everyone.  But since they don't trust those users, they want to make sure they don't accidentally delete existing files.  So they want to prevent the untrusted users from deleting files, but still be able to make new ones and change existing ones.  They also want to make it so that a group of people *are* able to delete those files.  

It doesn't help that we have a former Microsoft employee who was quick to point out that this would be trivial if our file share were running Windows Server.  Windows has advanced permission options that allow you to specify that a user can create, modify, but not delete files.  I haven't found anything that matches that in Linux, at least as far as a samba share with Linux file permissions goes.  There's ACLs, but they don't offer the flexibility that Windows does.

Does that help?  Any other details I can provide?

---

### Post by emptythevoid on 2011-06-21
Any takers?

---

### Post by CaptainMark on 2011-06-21
i think your trying the impossible, to delete files counts as a write so to give someone permission to create and edit you also give them permission to delete, i would love to be proven wrong but like baarn says if someone wanted to delete a file they would just open it and remove the contents, i think an alternative would be to periodically sync this shared directory to another storage device which only you have write permissions to, possibly using rsync, you could then re sync files back periodically so if someone does remove them, they would come straight back

---

### Post by stephen730 on 2011-06-22
Further more, if you can create a file and modify them, you can always overwrite blank files to replace them. This makes what you are doing impossible. Either read only or full write. YOU can do this type of setup with a FTP server. What you are looking to do would require either rsync, and using SSH to login, SCP which is secure copy over ssh, or FTP. All can be scripted from a command line both in windows and linux so you can make batch files. 

If you use captainmark's solution to rsync, keep in mind that if they make legitimate changes (modify) like you suggest, then their changes would simply be overwritten by that rsync. At least if you do SCP you can set up auditing as well and find out which one of them deleted the file. If its a work network, or a local network, then you can just call them out and let everyone know who's fault it was that the file got deleted and that might make them less intent on deleting.

---

### Post by emptythevoid on 2011-06-23
Thanks guys for the advice.  I, too, thought that I was asking the impossible.  We backup our server (including the directories in question) to an external hard drive, so if something did get accidentally deleted, they can be retrieved from the backup, but I understand what you're suggesting with rsyncing.  Unfortunately, we want the file to remain editable by those that would be making changes to it.  The managers specifically wanted this permission setup to prevent people from accidentally deleting the contents of the directory (they were unconcerned with someone blanking out a file and saving it).  The files are broken up  into multiple nested folders, so for now I have the nested directories marked read-only, with just the files writeable.  The worst that could happen is files in only one directory get deleted, but a careless person can't remove the entire directory structure and all it's files at once - they'd have to dig down into each nested directory.

Thanks for confirming that I understood the write-but-not-delete wasn't possible this way.  I appreciate the info!

---

### Post by idoitprone on 2011-06-24
I heard my teacher once.

Classic mail servers use directory scheme this execute and write without read.

The people can write, but they are blind after they created file, and the cannot enter the directory without read permissions. let just hope they do know the file name

I think this is what you wanted?

---

