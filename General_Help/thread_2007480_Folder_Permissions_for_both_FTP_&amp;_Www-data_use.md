---
title: "Folder Permissions for both FTP &amp; Www-data users?"
date: 2012-06-20
forum: General Help
---

### Post by matty231 on 2012-06-20
Gday everyone! Im new here... but used ubuntu for nearly ayear now!

I've been uploading files to a folder using an FTP user within my web directory : httpdocs/files... 

  But when my php script goes to move these files to a new directory it  fails, the files are uploaded with permissions 'rwx rw- rw- '... My  rename() function in PHP does not work...
  I've added the FTP user to group www-data using 'sudo usermod' and changing the owner using 'chown' with no luck...


My commands: chown -R www-data:www-data folder
and...              chgrp -R www-data folder

 

  Each time I want to upload FTP files ill need to set the ftp user to  the owner then to use the PHP script the www-data user will need to be  set as owner.


  Any way I can fix this please? It's doing my head in, I can't find a way around this. 
  Im on an UBUNTU VPS. I was on shared hosting and there was no issue there. 



Thanks.

---

