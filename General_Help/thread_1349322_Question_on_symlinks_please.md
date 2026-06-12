---
title: "Question on symlinks please?"
date: 2009-12-08
forum: General Help
---

### Post by listerdl on 2009-12-08
Hi I posted a similiar thread yesterday and learnt alot but I still havent fixed it!

My machine dual boots ubuntu and windows 7 - both can read the same NTFS partition. I would like for both systems to share the same dropbox folder, ('dropbox' is a cloud snycing application). 

In Windows when installing the program it forces me lable the application as "My Dropbox" and in Ubuntu is labels the foler as "Dropbox" - i.e. missing the "My"

To get the program to point to the same location in either OS, I understand that the best thing to do is to create a symlink in ubuntu to point to 'correct' windows "My Dropbox" folder.

Here is my problem....

My ubuntu dropbox is located here: /home/henry/Documents/Dropbox

Do I therefore do this code?

ln -s /home/henry/Documents/Dropbox/home/henry/media/storage/My Dropbox

so in the above example: ln -s /home/henry/Documents/Dropbox/ *takes the link to the correctly located folder and then the remaining code: *home/henry/media/storage/My Dropbox takes it to the place where I would like for the sync to occur.

Am I doing something wrong here? It doesnt work :(

When I do the above in terminal it simply returns without doing anything - no error and no message? Just returns....

THANKS!

---

### Post by KeLa on 2009-12-08
Instead of 

> **listerdl said:**
> 
ln -s /home/henry/Documents/Dropbox/home/henry/media/storage/My Dropbox


try this way

```
ln -s /home/henry/Documents/Dropbox "/home/henry/media/storage/My Dropbox"

```

This because of space in "My Dropbox" folder name.

---

### Post by listerdl on 2009-12-08
How do I remove symlinks and folders that might have symlinks connecting folders?

Thanks!

---

### Post by bchurchill on 2009-12-08
> **listerdl said:**
> How do I remove symlinks and folders that might have symlinks connecting folders?

Thanks!

To remove a symbolic link, you just issue 

$rm name_of_symbolic_link

In a given directory you can tell which files are symbolic links by running ls -l.  The symbolic links will have an arrow pointing to the location they link to.

I'm not quite sure what you mean by removing folders that might have symlinks connecting folders.  Is there something more specific you're trying to accomplish?

---

### Post by akashiraffee on 2009-12-08
> **listerdl said:**
> folders that might have symlinks connecting folders?

If you mean find all the symlinks to "myfile", you can't do it by checking myfile.  So that means you have to recurse thru the entire filesystem, or the parts of it where you think there could be a link.   There is a great solution, involving the inode number and "find -follow", here:

[http://ubuntuforums.org/showthread.php?t=90970](http://ubuntuforums.org/showthread.php?t=90970)

"stat" and "ls" will reveal where an individual link goes to.

---

### Post by listerdl on 2009-12-08
This was the output - 

Does this mean that below applies to al my dropbox symlinks or is this for every symlink on my machine?

Thanks!

drwxr-xr-x 2 henry henry 4096 2009-12-08 13:32 Desktop
drwxr-xr-x 2 henry henry 4096 2009-12-08 13:32 Documents
drwxr-xr-x 5 henry henry 4096 2009-12-08 13:52 Dropbox
drwxr-xr-x 2 henry henry 4096 2009-12-06 01:09 Music
drwxr-xr-x 2 henry henry 4096 2009-12-06 01:09 Pictures
drwxr-xr-x 2 henry henry 4096 2009-12-06 01:09 Public
drwxr-xr-x 2 henry henry 4096 2009-12-06 01:09 Templates
drwxr-xr-x 2 henry henry 4096 2009-12-06 01:09 Videos

---

### Post by KeLa on 2009-12-09
Here is sample what symbolic link looks with ls -l

lrwxr-xr-x 1 henry henry    16 2009-12-09 07:12 Dropbox -> /home/henry/media/storage/My Dropbox

So in the beginning of the line there is l = link instead of d = directrory and
after "->" is the target of the link.

---

