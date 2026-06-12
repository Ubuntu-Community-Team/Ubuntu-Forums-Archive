---
title: "Change Permissions Directories, Sub Folders and Files"
date: 2011-08-14
forum: General Help
---

### Post by Ed_Ziffel on 2011-08-14
Using Ubuntu 10.04 LTS.  Have lamp installed and all works fine with lamp.  Using my own php libraries.  Issue: when ever a new site is started and I copy and paste the libraries into the new site, ie. /var/www/my_new_site.com, the permissions go south and I wind up having to manually reset the permissions for every folder and file manually. Now that I've got sixty or seventy files/folders, this is not viable.  If I gksudo nautilus, and cut and paste the files into the new website folder, then all the permissions get set to Owner root, Access; create and delete files - Group: root, File access: access files - Others: Folder access: Access files.  

Have done the guess-a-permission thing in the terminal.  Can get all working but there has got to be a better way to assign permissions to a directory, its sub-folders and files.  Manually changing the permissions for every file and folder every time is beyond Mickey Mouse to the point of making using Windows to develop with seem like a good thing.  

I need the permissions for the copied directory, its sub-folders and files to be:  Owner: root, Folder access: Create and delete files -
Group: "MY User Group/"MY USER" Folder access: Create and delete files - Others Folder access: Access files.  Also need read and write permissions for all the files in the directory for root and my user/user group.  How does one set all permission for the files, folders and sub-folders in a given directory in the with the least amount of commands?  Could not having the user/user group set up properly effect things?

---

### Post by WyleECoyote on 2011-08-14
try:

$ sudo chown -R username:groupname /path/to/folder

chown = change owner
-R = recursively
username:groupname --> may be the other way round :D but you get it ;)

you can also use chmod to change attributes recursively nearly the same way

---

### Post by Ed_Ziffel on 2011-08-14
Thanks WyleECoyote,

The part I was missing was the -R.

so from root at the prompt;

cd var
cd www
sudo chmod 775 -r myfile.  where myfile is the directroy?  Is that right.

will work it out using the info at 
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://manpages.ubuntu.com/manpages/lucid/man1/chown.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/chown.1.html)

Looks like I'll be doing some cut and paste and seeing what pops up.

Thanks

---

### Post by WyleECoyote on 2011-08-14
yeah looks right to me, the easiest way to learn the shell is to use it most often so I suggest that for a while you should do everything in terminal that you would normally do in gui especially running programs, many times you may even find problems you never knew existed and some times fixing those problems will also fix problems you know exist ;)

---

