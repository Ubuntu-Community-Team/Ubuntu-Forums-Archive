---
title: "Error While Copying a File"
date: 2012-10-04
forum: General Help
---

### Post by kiusau on 2012-10-04
Question:  What does it mean when you are not permitted to copy a file into a system file folder?  How do you over come the problem?

Background:  I recently installed the latest versions of Apache and PHP into my Ubuntu OS.  The installation appears to have been successful, but I am now having my doubts.  For, when I attempt to copy simple text files with the .php extension into my var/www/ folder I am rejected -- this, despite, my having set full permissions for each and every folder along the directory path to the file.

---

### Post by Lars Noodén on 2012-10-04
It still sounds like the permissions need tuning.  What are the current permissions like?

```

ls -ld /var/www

```

---

### Post by kiusau on 2012-10-04
It is true that I have only changed the permissions for the User and Group.  I did not change the permissions for Other, as Other does not appear to be involved in the operation.

Is it being suggested that I must change the permissions of Other as well, because the file was not created by User and Group?

---

### Post by Lars Noodén on 2012-10-04
Other should be left alone.  It's only the Group that is relevant  and safe to work with.  Again, what are the current permissions like?

```

ls -ld /var/www

```

---

### Post by kiusau on 2012-10-04
OK. I have now provided RWX permissions for the entire directory chain and was able to copy the file.  Now, I am concerned that I have created a huge security breach

What is a good document to study about security in the File System?

---

### Post by Gregorybekkers on 2012-10-04
> **kiusau said:**
> OK. I have now provided RWX permissions for the entire directory chain and was able to copy the file.  Now, I am concerned that I have created a huge security breach

What is a good document to study about security in the File System?

It differs on what your group is. 
Just keep in mind that least privillage is best. 
If you cannot copy files in there from a regular user thats normal. 
Just use sudo.

---

### Post by Lars Noodén on 2012-10-04
> **kiusau said:**
> OK. I have now provided RWX permissions for the entire directory chain and was able to copy the file.  Now, I am concerned that I have created a huge security breach

What is a good document to study about security in the File System?

You probably have.  Can you please post the output of 'ls -ld' for your directory.  It would give much needed context for helping.  

If you want to read about file permissions, one place to start would be the community documentation:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by kiusau on 2012-10-04
Gregory:  I did use *sudo*, but not for the purpose of copying; rather, for the purpose of changing the permissions of the necessary File System folders.

Does the copy command work for both folders and files?  I did not think to do this, as my effort was focused on my inability to perform a very simple Desktop operation.

---

### Post by kiusau on 2012-10-04
I am reluctant to provide with the results for the ls -ld command, as I fear that it would expose me to the web even more than I am already currently exposed.  I can say this, though, everything that I changed to rwx was originally set to r-x.  I checked the permissions before I changed them.

I am now running into a new difficulty, however.  I cannot access the files that I copied into the folder via my web browser using [http://localhost](http://localhost).  Is there an option by which I can tell chmod to set permissions for all of the files and folders in a single directory?  

The copied files are all practice files for which I really do not care about security -- well, at least not for the moment.

By the way, thank you for the link.  I hope it has something in regard to the File System folders.

---

### Post by Lars Noodén on 2012-10-04
Ok.  Then here are some generic instructions for working with group permissions:
[http://ubuntuforums.org/showpost.php?p=11714082&postcount=2](http://ubuntuforums.org/showpost.php?p=11714082&postcount=2)

An important part is the set gid bit.  It's also important that the web server itself not have write access to the directories it is serving up.

---

