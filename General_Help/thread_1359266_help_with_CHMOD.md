---
title: "help with CHMOD"
date: 2009-12-19
forum: General Help
---

### Post by opigss on 2009-12-19
well im abit new with ubuntu, so after few days I rly get bored with starting .html files from windows partition and then get windows where ask me what i want with this file:   run / run in terminal / display / cancel  
so I asked my brother to hellp me with this and he send me on email some kind of solution: 

said to go in terminal, naviget into that folder and paste this:
chmod -R ugo-x *

and I did mastake in rush - i pasted this in terminal without going into that folder - so that looked like this
marko@kompjuter:~$  chmod -R ugo-x *

and after it... i sow lots of text... and i figured out when sow it that i did mastake... so after it, I couldnt save enyfile in my document folder in ubuntu, or video or picture, so I did restart, but after it I lost all documents from my desktop (some .odt files and flash files)

Well question is, how to "undo" this command and maybe return my files back.??? Is it possible... My bro is not answering on the phone so if someone can help me soon... Rly thx alot!

btw. If i made mastake and put this post in wrong category, admis plz put it somewhere where it should be and give me link in pm (im new in this forum too  :))   )

Thx 
Marko

---

### Post by arvevans on 2009-12-19
Using command-line commands in terminal mode is powerful, but possibly  unsafe unless you understand how the commands work.  There are "man pages" (manual pages) for almost all command-line functions.  In the case of "chmod" you can open a terminal window and at the prompt, enter "man chmod" which will then show the user manual page explaining how to use the "chmod" command.

---

### Post by oldfred on 2009-12-19
Your command -R recursively changed all files and directories below your location for users, groups, & other users to -x or remove execution. On directories that prevents you from doing anything.
The problem is you may not want  +x on everything, but only those things you want to execute or write to.

I would try this just to do the top level directories (no -R for recursive). But it will also change any files you have in the top level and not change any lower level directories.

chmod ugo+x *

If you do ls -l you will see your permissions. These are mine for just a a few of my top level ( I have links to a data partition):
drwxr-xr-x 2 fred fred  4096 2009-12-15 17:55 Desktop
lrwxrwxrwx 1 fred fred    30 2009-12-07 23:38 Documents -> /usr/local/fred/data/Documents
lrwxrwxrwx 1 fred fred    30 2009-12-07 23:39 Downloads -> /usr/local/fred/data/Downloads
lrwxrwxrwx 1 fred fred    34 2009-12-08 12:41 eclipsetrader -> /usr/local/fred/data/eclipsetrader
-rw-r--r-- 1 fred fred   167 2009-11-18 18:21 examples.desktop


Well if the files were in a windows partition you cannot chmod them you can only change permissions by mounting them differently. The default mount in Karmic seems to require more permissions. 
Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

---

### Post by opigss on 2009-12-19
Ty alot for explanation, Ill try to do this and hope the best. (Btw. I managed to manualy change permission status for me from "no acces" to "full read/write" in folder desktop - and then i sow all files that had there... and did it also in couple more folders, but now ill try ur solution and see will it help) 
Anyway, again, rly thx!

---

