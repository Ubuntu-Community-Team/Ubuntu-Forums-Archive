---
title: "Cannot Run Shell Scripts for Truecrypt"
date: 2011-10-08
forum: General Help
---

### Post by johntkucz on 2011-10-08
Hi,
I downloaded a shell script of Truecrypt and although I've installed it before on another machine and another version of ubuntu, I can't install it.  The option to "run in terminal" is not available upon right-clicking or anything.  Even when I choose to run in other application, Terminal is not listed.  Also using "./" from the command line results in "command not found".  Terminal does exist I can run the application but can't get it to run the shell scripts.  I've tried source code, console-only, and setup versiosn.

---

### Post by cyb3r_sn4k3 on 2011-10-08
Is it executable? chmod +x SCRIPT if its not.

---

### Post by johntkucz on 2011-10-08
> **cyb3r_sn4k3 said:**
> Is it executable? chmod +x SCRIPT if its not.


Hey cyb3r!

Well I loved the concise CLI response.  Some weird thigns are going on.  That was a brilliant suggestion (it didn't have executuble permissions), but when I right click menu and try to check "run as executable" OR run chmod +x scritname from cli the permissiosn don't change and the checkbox "unselects"! my username is chown owner of script.

---

### Post by johntkucz on 2011-10-08
Ah!! Okay, brilliant. I figured it out but would appreciate some more explanatory information.

Ubuntu is installed on a windows volume via wubi (I likely will change this to its own partition possibly in the future).  

the shell script file was located on a scratch disk /media/scratch_disk_name and for some reason on that location no permissiosn could be changed (but it didn't say permission denied it just wouldn't change the permissions.  Was this because of wubi?  The partition was a partitio nof the internal HD).

Anyways, I copied it to desktop (which is still located in /host/home/username/Desktop and then permissions could be controlled 100% normally.  What's up with that behaviour? 

Anyways, thanks again!

---

### Post by johntkucz on 2011-10-08
Possibly, original prob SOLVED (shell script executed and installed).  But am wondering what was up with that behaviour of not being able to change permissiosn on that /media/internal_hd_partition.  ubuntu is installed via wubi so everything is ntfs file system (I thought it could be somethign with that) but it worked on /home/Desktop

---

