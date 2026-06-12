---
title: "Hard disk full, can't delete backup folder"
date: 2009-11-21
forum: General Help
---

### Post by John RG on 2009-11-21
SOLVED

Grrr, I mucked up. Ran Simple Backup but couldn't work out how to save the backup straight to a subdirectory on an external drive. (Next time will just backup to external drive and then move the file.) Filled up my local hard drive. A 'senior moment'. Now I'm trying to recover without doing a reinstall because my backup didn't work...

When I start up I get to the login screen and it tells me I have an "Install Problem - the configuration defaults for Gnome Power Manager have not been installed properly". (IBM T43 laptop). Can't get past that. Assume this is computer saying "my hard disk is full, you've mucked me around, go away".

So, I boot off Karmic CD. 'Places' shows my hard drive as '58 GB Filesystem'. 23 items, Free space: 0 bytes.  Go to /var/backup and find I don't have permission. Use bad words. Read forums.

Alt F2 to open terminal. 'sudo nautilus'. Hard drive now shown as '247b1927-c509-4f08-a7e5-a054f2120bd1'. (Marvels at the friendliness of this...) 

var/backup shown as empty. (I may have deleted it in an earlier attempt. I'm recreating my actions as I type this on another pc running a satanic operating system.) var/backups is also empty. Use more bad words. (Quietly, wife asleep in next room.) Hunt around on disk and delete various 'tmp' files and folders but still can't create space on hard drive. When I try and open 'Trash' get a 'this operation is not supported error'. Search drive for 'Trash'. Find 463 items, all of which are image files of various sorts.

Try another thing. Open terminal. Type 'cd 247b1927-c509-4f08-a7e5-a054f2120bd1' (without quotes). Get bash error 'no such file or directory'. Can't work out how to change the directory from ubuntu@ubuntu:~$ to my hard drive.

When I type ls, I get in fancy font 'Desktop Documents Downloads...'.

Try various combos of cd with ~, quotes etc. Nothing works.

Tried using "Disk Usage Analyzer" from the live cd. It shows me as using 52 GB with 2 GB available, but '/' (the top level) is only showing 9GB.

Throws ego at mercy of forum. I am near certain that the aborted backup files are there somewhere but I don't know where to look or how to blow them away.

SOLVED! Found an answer in a thread on Gnome Power Mgmt tools. It's a problem with 'Simple Backup'. Will find another means to backup.

---

