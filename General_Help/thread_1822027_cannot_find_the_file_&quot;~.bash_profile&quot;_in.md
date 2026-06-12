---
title: "cannot find the file &quot;~/.bash_profile&quot; in the ubuntu"
date: 2011-08-10
forum: General Help
---

### Post by crazy hatter on 2011-08-10
hey friends,
           I just can't find the file which named '.bash_profile' in my home directory.since i am learning to write the shell script,i need to make some changes in that file.could you give me some help? thanks

---

### Post by Smart Viking on 2011-08-10
If you need it and it's not there, you can simply create it:
```
touch $HOME/.bash_profile
```

Maybe .bashrc is what you're looking for, which is executed every time when a new shell is opened, .bash_profile only executes when you log in.

---

### Post by Wim Sturkenboom on 2011-08-10
Just to make sure :

You understand that it is a hidden file ? If not, you must make them visible (e.g. with the -a option of *_ls_*)

```

wim@ubuntu-desktop01:~$ ls -**[COLOR="Red"]a[/COLOR]**l |grep bash
-rw-------  1 wim  wim  5989 2011-08-08 11:58 .bash_history
-rw-r--r--  1 wim  wim   220 2011-07-19 09:41 .bash_logout
-rw-r--r--  1 wim  wim  3103 2011-07-19 09:41 .bashrc
wim@ubuntu-desktop01:~$ 
```

This is taken from a more-or-less fresh install and it's indeed not there. So follow the above advise or just cerate it with the editor of your choice.

---

### Post by whatthefunk on 2011-08-10
Yes.  Its probably the .bashrc that you want.

---

### Post by WorMzy on 2011-08-10
As Wim Sturkenboom said, that file is a *hidden* file; all files and folders that begin with a full stop (.) are. You can press Ctrl+H while in most file managers to show hidden files and folders.

---

