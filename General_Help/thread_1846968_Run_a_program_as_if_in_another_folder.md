---
title: "Run a program as if in another folder?"
date: 2011-09-19
forum: General Help
---

### Post by gennoveus on 2011-09-19
Hi,

Sorry about the nonsense title, I didn't really know how to explain my problem in so few words.

My problem is this:
I have a program that I always run from the terminal by cd'ing to that folder and running it as you would - ./[filename]. The problem is that I want to add a shotcut to the main menu to run this program, but it doesn't work because the executable searches for some config files that are in the same folder as it, and so when it runs it from the menu shortcut it looks for the config files in the wrong place.

So how can I write the main menu command so that it runs it as if I had run it from it's own folder ... ?

I hope I'm making sense. It I'm not being very clear then please let me know and I'll try be clearer.

Thank you!

p.s. I just read my own post and it really isn't very clear so I'll demonstrate:

~$cd folder1
~/folder1$cd folder2
~/folder1/folder2$./theprogram

This runs fine.

~$folder1/folder2/theprogram
bsettings.cpp, 52: Failed to open settings file: settings.cfg.
main.cpp:1109 - ERROR: Error attempting to initialize settings data.
~$

This causes problems. :(

Again, thank you for your help!

---

### Post by raja.genupula on 2011-09-20
```
assassin@raju-xubuntu:~$ mkdir r
assassin@raju-xubuntu:~$ cd r
assassin@raju-xubuntu:~/r$ mkdir r1
assassin@raju-xubuntu:~/r$ cd r1
assassin@raju-xubuntu:~/r/r1$ gedit h.sh
assassin@raju-xubuntu:~/r/r1$ chmod +x h.sh
assassin@raju-xubuntu:~/r/r1$ ./h.sh
hi
assassin@raju-xubuntu:~/r/r1$ cd
assassin@raju-xubuntu:~$ 
assassin@raju-xubuntu:~$ ./r/r1/h.sh
hi
assassin@raju-xubuntu:~$ 

```

i hope that gonna help you man

---

### Post by sisco311 on 2011-09-20
> **gennoveus said:**
> 
So how can I write the main menu command so that it runs it as if I had run it from it's own folder ... ?


```
sh -c 'cd /path/to/dir && ./command'
```

Where */path/to/dir* is the full path to the directory and 
*command* is the name of the command.

---

### Post by raja.genupula on 2011-09-20
> **sisco311 said:**
> ```
sh -c 'cd /path/to/dir && ./command'
```

Where */path/to/dir* is the full path to the directory and 
*command* is the name of the command.


yeah ,  but we need this if we are running the program from unsupported UNIX file systems like NTFS and FAT or FAT32 .

---

### Post by gennoveus on 2011-09-20
Thanks guys!!!

sisco311, that's a good idea! 

I'm running it from a ext4 partition so no problem.

Thanks again!

---

### Post by raja.genupula on 2011-09-20
aah we are glad that you got what you want , could you please mark the thread as solved .

---

### Post by gennoveus on 2011-09-20
> **raja.genupula said:**
> aah we are glad that you got what you want , could you please mark the thread as solved .

Sorry raja, I totally forgot.

It should be marked solved now. (you guys must get sick of reminding people about that!)

---

