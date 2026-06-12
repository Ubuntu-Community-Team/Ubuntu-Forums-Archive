---
title: "I need CMD line codes to back up 3 things. Help please"
date: 2011-10-13
forum: General Help
---

### Post by maddbaron on 2011-10-13
I'm upgrading to the newest version with a fresh install but I'd like to back up some things in txt form so i can move them to an external hard drive.

I need to backup

1. My terminal codes
2. My current source list (ppa's etc)
3. Currently installed applications

Can someone tell me the terminal codes to do these 3 things?


Thanks in advance

---

### Post by gmargo on 2011-10-13
1. I'm not sure what you mean by "my terminal codes".  Perhaps you should just backup your entire home directory.

2. Current source/ppa list: all contained under the **/etc/apt/** directory.

3. Currently installed applications: run "dpkg --get-selections"  (or "dpkg -l").

---

### Post by oldos2er on 2011-10-13
> **maddbaron said:**
> I'm upgrading to the newest version with a fresh install but I'd like to back up some things in txt form so i can move them to an external hard drive.

I need to backup

1. My terminal codes

```
cp .bash_history .bash_history.old
```

> 2. My current source list (ppa's etc)

```
cp -r /etc/apt/sources.list.d/ . && cp /etc/apt/sources.list .
```

> 3. Currently installed applications

```
dpkg --get-selections > apps.list
```

---

### Post by maddbaron on 2011-10-13
> **oldos2er said:**
> ```
cp .bash_history .bash_history.old
```



```
cp -r /etc/apt/sources.list.d/ . && cp /etc/apt/sources.list .
```



```
dpkg --get-selections > apps.list
```

thanks and these would save to the home folder by default yes?

---

### Post by effenberg0x0 on 2011-10-13
cd (changes to your default directory, your user folder)
cp .bash_history .bash_history.old (created a copy, with the different extension(.old), but still at your directory).
cp -r /etc/apt/sources.list.d/ . && cp /etc/apt/sources.list . (the dot "." means "Your current directory". That means thae files will be saved to the directory you are when when you invoke the commands. But your first command was "cd", so you are at your directory. These is where the files will be saved).
dpkg --get-selections > apps.list (The output is redirected to a file with no directory specification, so it can only be in the same directory as the command was issued. But, as you ran "cd" as the first command, apps.list will be saved at your directory.)

ls -lha (will show you the backed up files)

---

