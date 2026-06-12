---
title: "Changing from user@Laptop:/$ to user@Laptop:~$"
date: 2011-01-22
forum: General Help
---

### Post by whatthefunk on 2011-01-22
In the terminal, after I change directories and wish to go back to the main directory, I end up with a /$ rather than a ~$.  In order to do certain commands, I need to have a ~$.  How do I change between the two?  What exactly do these symbols mean?  Thanks

---

### Post by Smart Viking on 2011-01-22
"/" means you are in the root directory, while "~" means you are in your home directory.

---

### Post by whatthefunk on 2011-01-22
Why can I not do certain things from root?  For example, I wanted to view .bashrc and so typed:
less .bashrc
In / it says that there is no such file, but in ~ I can read the file.  

Im confused...

---

### Post by yetiman64 on 2011-01-22
> **whatthefunk said:**
> Why can I not do certain things from root?  For example, I wanted to view .bashrc and so typed:
less .bashrc
In / it says that there is no such file, but in ~ I can read the file.  

Im confused...
That's because the file .bashrc is located inside your home folder (or ~).

To view the file while at the root filesystem (/) then you would need to define the path to the file and specify an application to view it (from within the terminal "cat" is useful).

1st cd to root of the filesystem (working as a normal user that is)
```
cd /
```Now try (noting that ~ is a system variable which indicates your home folder)
```
cat ~/.bashrc
```The contents will show in the terminal with cat. The command could have just as easily used nano or gedit (text editors).

---

### Post by Dave_L on 2011-01-22
Tip: If you're not sure what directory you're in, the "pwd" command will tell you.

---

### Post by whatthefunk on 2011-01-22
Got it.  Thanks for the help!

---

