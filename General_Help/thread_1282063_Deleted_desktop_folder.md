---
title: "Deleted desktop folder"
date: 2009-10-03
forum: General Help
---

### Post by snakeman21 on 2009-10-03
Hi all.  

My wife runs Ubuntu 9.04, same as me.  Earlier today, she was deleting a few things, and accidentally deleted her desktop folder.  Now, her Documents, Music, Pictures, and Videos folders are defaulting to her desktop.  I tried restoring the Desktop folder from the trash, but it just put in on the desktop.  Basically, EVERYTHING that's in her home folder has a desktop icon now.  In other words, her desktop IS her home folder... How do I fix this?  She hates having icons on the desktop.

Thanks in advance!

---

### Post by Steel-Bunz on 2009-10-03
Did you try moving the files to some other folder?

Could you please post the output of the command "ls -l" from root directory?

---

### Post by mechro on 2009-10-03
I'm not sure but it sounds like deleting Desktop has activated Nautilus's "*desktop_is_home_dir*" parameter.

To change it back you could use the Gnome Configuration Editor. If it's not installed then go to Add/Remove Applications and install Configuration Editor.

Once it's installed, navigate to Applications-System Tools-Configuration Editor. In the Editor, navigate to apps/nautilus/preferences and uncheck the box for *desktop_is_home_dir*. Log-out and Log-in again to complete the change.

---

### Post by snakeman21 on 2009-10-04
Mechro:  

"desktop_is_home_dir"  Is already unchecked.


Steel-Bunz:

Output is:

```
shaina@jaunty:~$ ls -l
total 714152
drwxr-xr-x 5 shaina shaina      4096 2009-10-03 15:29 Documents
drwxr-xr-x 6 shaina shaina      4096 2009-08-28 17:53 Music
drwxr-xr-x 8 shaina shaina      4096 2009-09-19 14:31 Pictures
drwxr-xr-x 3 shaina shaina      4096 2009-10-03 21:39 Videos
shaina@jaunty:~$ 
```

---

### Post by Steel-Bunz on 2009-10-04
> **snakeman21 said:**
> Mechro:  

"desktop_is_home_dir"  Is already unchecked.


Steel-Bunz:

Output is:

```
shaina@jaunty:~$ ls -l
total 714152
drwxr-xr-x 5 shaina shaina      4096 2009-10-03 15:29 Documents
drwxr-xr-x 6 shaina shaina      4096 2009-08-28 17:53 Music
drwxr-xr-x 8 shaina shaina      4096 2009-09-19 14:31 Pictures
drwxr-xr-x 3 shaina shaina      4096 2009-10-03 21:39 Videos
shaina@jaunty:~$ 
```

I wanted to make sure that your home directory structure is not messed up. I am trying to understand where exactly these four folders you have listed are located.

Do you still have "/home/shaina" folder? Go to *Places -> Home Folder*. Nautilus window will open; let me know what does the location bar look like? Mine says "/home/username". Alternatively, you can use the command "pwd" in terminal which will list the 'present working directory'. This will tell us where these folders are located.

---

### Post by mechro on 2009-10-04
> **snakeman21 said:**
> Mechro:  

"desktop_is_home_dir"  Is already unchecked.



OK.

The *user-dirs.dirs* file in /home/user/.config could be messed up. Try solution in this thread...

[http://ubuntuforums.org/showthread.php?t=581498](http://ubuntuforums.org/showthread.php?t=581498)

---

### Post by snakeman21 on 2009-10-04
Steel-Bunz: 

pwd returns /home/shaina, and Nautilus does the same.

Mechro:  I'm on her laptop now, and I'll try the solution in that thread.  I'll let you know what happens.

EDIT:  HA! Victory is mine!  Thanks so much for that, it worked perfectly.  I didn't even have to do all that restarting nautilus crap... It didn't crash like I thought it would.  

Computers are frustrating.  Just when I think I know enough to fix just about any issue, I get a curveball.  But, that's why I love the open source community.  There's always someone who knows more than me that's willing to help.  My wife will be pleased.  Thanks again!

---

