---
title: "Robocopy Equivalent"
date: 2010-11-29
forum: General Help
---

### Post by TombstoneX on 2010-11-29
I am trying to find an equivalent to the command below. Basically what i need is the ability to make a copy of a directory to another directory, however, i need it to only copy the new files that haven't been copied. (please note that once the files are copied into the destination folder, they are going to be moved once again to a 3rd folder. I dont want a replica replaced into the destination folder)


Here is the original windows command:

---------------------------------

ROBOCOPY C:TorrentsComplete c:RenameSeries /NP /M /S  /LOG+:c:BatchesRename_series.log

Robocopy is a robust Microsoft file copying utility. Here is a breakdown of the first command:

C:TorrentsComplete is the source folder.

C:RenameSeries is the destination folder.

The /NP switch prevents robocopy from displaying the percentage copied complete which would fill up the log file with unnecessary information.

/M copies all files with the Archive attribute set and resets the Archive attribute (this flag allows us to only copy the new files that has arrived since the previous time we copied the files).

/S copies all the files in this folder and all subfolders

/LOG+:c:BatchesRename_series.log instructs Robocopy to create a logfile and keep adding to the file. As soon as the process is working properly this setting can be removed.

---

### Post by a-user on 2010-11-29
there is no archive attribute on linux filesystems as far as i know. but what you want you should achieve with teh following:

cp -uR source dest

the R option makes it recursive, the u option overwrites only if the source file is newer than the destination file (this substitutes archive attribute).

if you want to log do:
cp -uvR source dest > cp.log

v makes cp verbose and with "> cp.log" you redirect the output to the file cp.log.

edit: check manpage of cp for more infos, e.g. regarding preserving file permissions and other stuff. type "man cp" in console

---

