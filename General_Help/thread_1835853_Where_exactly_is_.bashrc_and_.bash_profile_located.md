---
title: "Where exactly is .bashrc and .bash_profile located?"
date: 2011-08-30
forum: General Help
---

### Post by padfootpak on 2011-08-30
I have been trying to learn bash scripting from linuxcommands.com and in one lesson they ask me to edit .bash_profile. They tell me that it will be located at home. but even after 


```
cd /home
ls
```i do not see the file there. 

One more thing. How do i open .bash_profile in pico or gedit?
Will this suffice?

```
pico .bash_profile
``` Or should I leave the dot out?

---

### Post by Drenriza on 2011-08-30
try
```
cd ~
```
```
ls -a |grep bashrc
```

---

### Post by eentonig on 2011-08-30
> **padfootpak said:**
> 
```
cd /home
ls
```i do not see the file there. 



```
ls -al $HOME
```

Which is a shortcut for /home/<username>


And to edit, you can use any text editor you want. 

vi, gedit, nano, pico. But you will have to include the "." in the filename. Otherwise, you'll create a new file.

---

### Post by mcduck on 2011-08-30
> **padfootpak said:**
> I have been trying to learn bash scripting from linuxcommands.com and in one lesson they ask me to edit .bash_profile. They tell me that it will be located at home. but even after 


```
cd /home
ls
```i do not see the file there. 

One more thing. How do i open .bash_profile in pico or gedit?
Will this suffice?

```
pico .bash_profile
``` Or should I leave the dot out?

They are located in your home directory (which is /home/username, not /home). Also any file or directory with a name that starts with a dot is a hidden file, so a simple  "ls" will not show them, you need to use "ls -a" instead. (If you want to see hidden files in the Nautilus file manager just press Ctrl-h)

For the command to open the file in editor, that would work if you are in your home directory when you run it. For a more generally working approach you need to specify where the file is. ("pico ~/.bash_profile"). And no, you can't leave out the dot, it's part of the file's name.

---

