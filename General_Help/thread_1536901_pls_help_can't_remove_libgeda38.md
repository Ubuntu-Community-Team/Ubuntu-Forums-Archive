---
title: "pls help can't remove libgeda38"
date: 2010-07-22
forum: General Help
---

### Post by Mudsucks on 2010-07-22
I'm stuffed.

I have 2 packages that return errors when I try to remove them. This stops my Update and Software Center from working. Even wost it stops me from fixing a problem with Evolution the gives "Error while generating message list" when I try to get mail. :(

Please someone help me.

The following NEW packages will be installed:
  sqlite3
0 upgraded, 1 newly installed, 2 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/26.5kB of archives.
After this operation, 1,020kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 195713 files and directories currently installed.)
Removing libgeda38 ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing libgeda38 (--remove):
 subprocess installed post-removal script returned error exit status 2
Removing libgeda-common ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing libgeda-common (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 libgeda38
 libgeda-common
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Mudsucks on 2010-07-22
update; fixed software center with "sudo apt-get check" uninstalled gEDA and hence fixed libgeda-common and libgeda38 faults.

now Evolution, 

 cd ~/.evolution/mail ; for i in `find . -name folders.db`; do echo "Rebuilding Table $i"; sqlite3 $i "pragma integrity_check;"; done
Rebuilding Table ./local/folders.db
The program 'sqlite3' is currently not installed.  You can install it by typing:
sudo apt-get install sqlite3
Rebuilding Table ./pop/petergilbert@pop.ihug.co.nz/folders.db
The program 'sqlite3' is currently not installed.  You can install it by typing:
sudo apt-get install sqlite3
Rebuilding Table ./vfolder/folders.db
The program 'sqlite3' is currently not installed.  You can install it by typing:
sudo apt-get install sqlite3
[email]mudsucks@mudsucks-laptop:~/.evolut[/email]ion/mail$ sudo apt-get install sqlite3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  sqlite3-doc
The following NEW packages will be installed:
  sqlite3
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/26.5kB of archives.
After this operation, 115kB of additional disk space will be used.
Selecting previously deselected package sqlite3.
(Reading database ... 195744 files and directories currently installed.)
Unpacking sqlite3 (from .../sqlite3_3.6.22-1_i386.deb) ...
Processing triggers for man-db ...
Setting up sqlite3 (3.6.22-1) ...
[email]mudsucks@mudsucks-laptop:~/.evolut[/email]ion/mail$ cd ~/.evolution/mail ; for i in `find . -name folders.db`; do echo "Rebuilding Table $i"; sqlite3 $i "pragma integrity_check;"; done
Rebuilding Table ./local/folders.db
*** in database main ***
On page 4 at right child: invalid page number 235
Error: database disk image is malformed
Rebuilding Table ./pop/xxxxxxxxxxx@pop.ihug.co.nz/folders.db
ok
Rebuilding Table ./vfolder/folders.db
ok
[email]mudsucks@mudsucks-laptop:~/.evolut[/email]ion/mail$ sqlite3 ~/.evolution/mail/local/folders.db "pragma integrity_check;"
*** in database main ***
On page 4 at right child: invalid page number 235
Error: database disk image is malformed
[email]mudsucks@mudsucks-laptop:~/.evolut[/email]ion/mail$ 

off to google some more.....;)

---

