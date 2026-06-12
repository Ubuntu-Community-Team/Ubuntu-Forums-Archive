---
title: "Read Only"
date: 2011-01-29
forum: General Help
---

### Post by Mardok42 on 2011-01-29
I just installed Ubuntu server yesterday, and then proceeded to install the desktop as well.  Both seem to be working great, with one exception.  The entire file system is read only in the desktop environment.   I am listed as an administrator, heck I even added myself to the root group.  

I can change things by opening the terminal and entering the sudo command, but being able to change documents out of terminal would be great.

---

### Post by tredegar on 2011-01-29
Please click the [Go Advanced] button beneath the Quick Reply box.

Then paste the output of the following commands between "Code Tags" (the # icon on the advanced reply editor)
```
ls  -al   /home
who
```
Thanks.

---

### Post by Mardok42 on 2011-01-29
K here is what I got

```

ls -al  /home
total 12
drwxr-xr-x   3 root   root   4096 2011-01-28 16:06 .
drwxr-xr-x  21 root   root   4096 2011-01-29 02:35 ..
drwxr-xr-x  26 mardok mardok 4096 2011-01-29 06:58 mardok

who
mardok tty7         2011-01-29 06:58 (:0)
mardok pts/0        2011-01-29 07:02 (:0.0)


```

---

### Post by tredegar on 2011-01-29
Thanks.

> The entire file system is read only in the desktop environment.
This is not the case: You have write access to all the files in your home directory. This is normal.

You do not (as the user **mardok**) have write access to the system files. This is normal, and part of linux's security.

If you wish, as an "administrator", to edit system files using a GUI editor you can launch one with root privileges with the command **gksudo gedit** in a terminal.

You should _not_ be a member of the group **root**. Please undo this change before you damage your system.

---

### Post by Mardok42 on 2011-01-29
Thank you for your help.  How do you launch a GUI with root privileges?  Because its either do that or change where I have been putting the website.

---

### Post by JKyleOKC on 2011-01-29
As he said, open a Terminal window and type **gksudo gedit** followed by Enter, to open the editor with root privileges. You can also use the command **gksudo nautilus** to open the file manager as root. Both are, of course, extremely dangerous since the system will not question any change you make -- not even if it destroys the system!

---

### Post by Mardok42 on 2011-01-30
New question then, should I put my web pages in a directory that is not part of root?

---

### Post by JKyleOKC on 2011-01-30
When I was experimenting with web pages on a local system, I added myself to the "www-data" group and that gave me write permission to the www-data directory and all of its subdirectories. You might look at the "users and groups" area of the system administration programs to see the exact group name and how to add yourself to the group...

---

