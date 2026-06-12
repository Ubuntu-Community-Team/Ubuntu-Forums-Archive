---
title: "Automatically display gedit files"
date: 2011-05-08
forum: General Help
---

### Post by johntkucz on 2011-05-08
Hi, running 10.04 netbook lucid lynx and I have couple of simple plain gedit text files.  Wheenver I open them I am always prompted "this is an executable file, with the the choice to
Run in Terminal
Display
Cancel
Run

how do i get these simple text files (which are not executables unless file type got messed up) just to automatically display in gedit (they're set to open wtih gedt app).

Thanks

---

### Post by erind on 2011-05-08
Open a terminal, change directory to where your files are, then remove the execution bit from them:

```
cd /full/path/to/files

chmod a-x filename1 filename2 ...
```Replace filename1, 2, 3 ... with their real names.

---

### Post by mikewhatever on 2011-05-08
In the file browser, open Edit->Preferences->Behavior Tab, check 'View executable files when they are opened' instead of 'Ask every time'.

---

### Post by johntkucz on 2011-05-10
> **erind said:**
> Open a terminal, change directory to where your files are, then remove the execution bit from them:

```
cd /full/path/to/files

chmod a-x filename1 filename2 ...
```Replace filename1, 2, 3 ... with their real names.

Hey mate!! I just did a blog post (coincidentally, well partially thinking it was related to this) so this is exciting; am eager to learn how to use chmod more effectively.

but after typing in your code or chmod 700 filename or chmod u=rw filename, I do ls -al and still get what looks like the same permissions (a lot of r-x.

What's "a-x" ??

does a = ugo?  could the above command be rewritten as 

ugo-x ??

wanting to learn more of this because I like using hte terminal.
Some read outs:

```
drwx------ 2 jtk jtk   4096 2011-05-10 11:35 .
drwx------ 4 jtk jtk   4096 2011-05-10 11:21 ..
-rwxr-xr-x 1 jtk jtk   7487 2011-05-10 11:21 blog_articles.txt
-rwxr-xr-x 1 jtk jtk   3082 2011-05-10 10:52 computertasks_and_internetlookup
-rwxr-xr-x 1 jtk jtk 103592 2011-05-10 11:35 copypaste_to_journal
-rwxr-xr-x 1 jtk jtk  27785 2011-05-09 00:01 emails
-rwxr-xr-x 1 jtk jtk   1943 2011-05-09 02:31 popp
-rwxr-xr-x 1 jtk jtk   2810 2011-05-08 17:45 would_like_to_do_today
jtk@netbookubu:/media/PENDRIVE/docs_bu_pendrive/docs$ chmod 700 blog_articles.txt
jtk@netbookubu:/media/PENDRIVE/docs_bu_pendrive/docs$ ls -al
total 160
drwx------ 2 jtk jtk   4096 2011-05-10 11:35 .
drwx------ 4 jtk jtk   4096 2011-05-10 11:21 ..
-rwxr-xr-x 1 jtk jtk   7487 2011-05-10 11:21 blog_articles.txt
-rwxr-xr-x 1 jtk jtk   3082 2011-05-10 10:52 computertasks_and_internetlookup
-rwxr-xr-x 1 jtk jtk 103592 2011-05-10 11:35 copypaste_to_journal
-rwxr-xr-x 1 jtk jtk  27785 2011-05-09 00:01 emails
-rwxr-xr-x 1 jtk jtk   1943 2011-05-09 02:31 popp
-rwxr-xr-x 1 jtk jtk   2810 2011-05-08 17:45 would_like_to_do_today
jtk@netbookubu:/media/PENDRIVE/docs_bu_pendrive/docs$ chmod g=r popp
jtk@netbookubu:/media/PENDRIVE/docs_bu_pendrive/docs$ ls -al
total 160
drwx------ 2 jtk jtk   4096 2011-05-10 11:35 .
drwx------ 4 jtk jtk   4096 2011-05-10 11:21 ..
-rwxr-xr-x 1 jtk jtk   7487 2011-05-10 11:21 blog_articles.txt
-rwxr-xr-x 1 jtk jtk   3082 2011-05-10 10:52 computertasks_and_internetlookup
-rwxr-xr-x 1 jtk jtk 103592 2011-05-10 11:35 copypaste_to_journal
-rwxr-xr-x 1 jtk jtk  27785 2011-05-09 00:01 emails
-rwxr-xr-x 1 jtk jtk   1943 2011-05-09 02:31 popp
-rwxr-xr-x 1 jtk jtk   2810 2011-05-08 17:45 would_like_to_do_today

```


tl;dr I'm running the chmod commands but it doesn't seem to be changing the permissions of the files.  Atleast I now know that that questi on (display, run, run in terminal, cancel) is symptomatic of the file having an execute permission! NICE! At least that bit is very helpful. thanks!! But still trying to eliminate (apparently) the e(x)ecutable permissions notation from user (or all, user, group, other). Thanks!

---

### Post by johntkucz on 2011-05-10
> **mikewhatever said:**
> In the file browser, open Edit->Preferences->Behavior Tab, check 'View executable files when they are opened' instead of 'Ask every time'.

Okay great, thanks mike, using this GUI preference of nautilus worked and now files open without the dialogue. Sweet. So my initial problem is SOLVED.

but now I'd like to be able to learn how to use chmod effectivley.

in short, I'd like to do a chmod and see r-w------ as a goal for permissions.  and the permissions don't seem to be changing.  Thanks a ton.

---

### Post by johntkucz on 2011-05-10
Should I relocate this to a new thread (?) because technically original problem is solved and new problem is chmod command in ternal runs, but doesn't apparently make any changes to any of the ugo permissions

---

### Post by Dave_L on 2011-05-10
Is /media/PENDRIVE a non-linux file system, such as FAT?  If so, the file permissions are determined by the mount settings, and cannot be individually changed.

---

### Post by erind on 2011-05-10
From your output it seems that you're using an external drive, possibly FAT or NTFS formatted, and as *Dave_L* mentioned, there's not much you can do about it. From a terminal type *sudo fdisk -l* or *df -T* to see what's the drive's file-system. In the example below the last line shows an USB drive FAT formatted.

```
$ df -T
Filesystem    Type   1K-blocks      Used Available Use% Mounted on
/dev/sda1     ext4   121836340  53003540  62643812  46% /
....
tmpfs        tmpfs     2012244     51124   1961120   3% /tmp
none         tmpfs     2012244       128   2012116   1% /var/run
[COLOR=Red]/dev/sdb1     vfat    31310864   1433264  29877600   5% /media/32GB_LEXAR[/COLOR]
$ 
```> **johntkucz said:**
> ...
What's "a-x" ??

does a = ugo? could the above command be rewritten as

ugo-x ??
 
Yes you can,  **a** stands for **ugo **(all). Here is a good article on unix file permissions:  
 
[http://www.unix.com/tips-tutorials/19060-unix-file-permissions.html](http://www.unix.com/tips-tutorials/19060-unix-file-permissions.html)

---

