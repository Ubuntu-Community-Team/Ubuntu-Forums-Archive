---
title: "Help Recovering Deleted Files......"
date: 2010-11-24
forum: General Help
---

### Post by amzium on 2010-11-24
Hi,   I have lost some folders that withhold some important files.   I where inside a folder doing chmod -R 777 * and chown -r (usrnamn) *  and all the folders that where inside that folder that where hidden became lost.   crush me as much as you like as the commands where probably THE most dumb one writen this age, but im really in need of help.  The files that are missing are a collection of 2 years of hard work.   Now Im going utterly nuts, when I try backtrack I cant manage to use it to find something, I try to compile sleuthkit I get an error. And I just feel damn'd helpless.  just an FYI the files that are important are .blend files and the regular tools to what I understand only apply to regular file types as .jpg .zip etc etc.....  Could someone please... Please..... help me.

---

### Post by oldfred on 2010-11-24
I recently used photorec to recover a bunch of files that disappeared. It also recovered the fragments of changes and in a few cases text files were mixed up.

I followed some of the instructions on sorting files but I still had lots of the same file (or minor differences) as I had edited & saved many times.

Testdisk & photorec
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://www.linux.com/archive/feed/56588](http://www.linux.com/archive/feed/56588)
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)

---

### Post by cwa on 2010-11-24
hey,

 First off, I have gone through the feeling of loosing data, I can relate. 


forgive insensitivity, but if you ran a recursive chmod and chown, can't you see the files doing ls -a or sudo ls -a. from my slight research, 777 sets the read and write and execute bits on the file. Did you remove them as well?

If you really deleted them and I am missing something:

OldFred is right, photorec and testdisk can work wonders. 

take a look at system recovery cd, it comes with both testdisk and photo rec on it. Boot off this cd and try to recover the files from your hard drive. If you have truly deleted your files, and if Linux works like Windows, you do not want to be downloading, compiling and installing software on the same partition as the lost files were on. 

hope that helps,
cwa

---

### Post by amzium on 2010-11-25
First of all thank you guys to take time writing me, appreciate it a lot.
I do not know how to reverse the commands really and I have tried all sorts of commands to view the files. Cause according to me, the should have just become un-viewable but no results.

The solution that looks the brightest at the moment where to make a custom pattern for "Foremost" based on the start and end in hexadecimal. The first try gave me a bunch of files but, I had setup the pattern on to low file size (200 kb), I cant really remember what the typical size of the files where but I put it to 100 mb to be sure.

I would really like to learn to reverse a command, do tell if you have the spare time

---

### Post by cwa on 2010-11-25
amzium,

With chmod, it changed file permissions, chown can change user/group  ownership of a file. thinking about it more, I am not sure why it  appeared to delete the files. Maybe I need to read up more about chmod  and chown though. 

the easiest way to reverse the chmod or chown command that I can think of is just to rerun the command and change the permissions  / ownership back.  If you no longer have ownership of the files, then you might have to be root / use sudo to change the file permissions back. 

in my last post, system rescue cd is a bootable rescue cd that can be downloaded from [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download) there are plenty of other rescue / live cds 

as far as a reverse for your command, here are some things I would try.

do a directory listing (preferably from the rescue cd) and do a ls -a to show any files including hidden files.  

or do a directory listing with inode numbers listed. I believe an inode is a number assigned by the filesystem to each file there. maybe the inode entry is there still but file name is not. 

otherwise, you might have to use foremost or testdisk or photorec to try and recover the files 

hope that helps.

---

### Post by cwa on 2010-11-25
amzium,

I tried recreating the situation by creating a directory containing visible and hidden files and directories. I could not get anything to become lost, in both runs (I did this twice) I could still access and see the hidden files and folders. 

Can you fill me in on a few more details of what happened and what the commands were? 

Also, 

ls -i will list the inode number of the file 
ls -d .[^.] will list hidden directories/(files?)
ls -a will list hidden files
ls -l will list file permissions

I also wondered if checking the log files /var/log/syslog /var/log/messages for starters will reveal any more what happend.

---

