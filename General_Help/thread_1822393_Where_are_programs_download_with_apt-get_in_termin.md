---
title: "Where are programs download with apt-get in terminal ?"
date: 2011-08-10
forum: General Help
---

### Post by lordmonkeyu on 2011-08-10
Hello,
As in topic. I have just installed qBittorrent with terminal with apt-get but I do not know where I can find it besides the Launcher and the panel on the top of the screen.

---

### Post by MG&amp;TL on 2011-08-10
Err...you mean you want to find where the program actually lives on the filesystem? It varies, but I usually find mine in /usr/bin.

---

### Post by lordmonkeyu on 2011-08-10
Ok thanks, that's what I wanted to know.
And btw: how can I check if it's not in the /usr/bin ? If i know where the programs is in the panel menu or how to launch it from the terminal but I do not know where it is in filesystem ?

---

### Post by MG&amp;TL on 2011-08-10
```
cd /
find -name 'name of your program.exe'
```This will take a while and may pull up multiple results and 'permission denied' Don't worry about 'permission denied' I think they are system files.

If you don't know the exact name of your program, use a wildcard (fill in the gaps for me)

e.g. to find cairo-dock, (dock application, may not be installed on your pc):

```
cd /
find -name 'cairo*.exe'
```I am sure you are capable of finding which result you need. :D

---

### Post by oldos2er on 2011-08-10
```
dpkg -L qbittorrent
``` will show where each file in the qbittorrent package is installed.

---

### Post by CatKiller on 2011-08-10
@MG & TL: there won't be a .exe, and* which* is better for finding where the executable is.

---

### Post by MG&amp;TL on 2011-08-10
@CatKiller-with a lot of respect for seniority, why won't there be an .exe? It works for me. Or is minecraft a .sh? I don't actually know what minecraft is, so there you go.

Oops, yeah, 'which' is much better. :oops:

---

### Post by CatKiller on 2011-08-10
Because .exe files are a Windows thing.

---

### Post by MG&amp;TL on 2011-08-10
Ah. OK, weird it showed up on Xubuntu as .exe? But running in Ubuntu, nothing shows up as expected. What file extension does Linux use then? Thanks, CatKiller, something new everyday. :D

---

### Post by matt_symes on 2011-08-10
Hi 

Linux does not use file extensions to identify the file type in the same way as windows.

To find the file type, at a terminal type

```
file <file_name>
```

I.E

```
matthew@matthew-laptop:~/my_documents/my_logons$ file free_index
free_index: ASCII text
matthew@matthew-laptop:~/my_documents/my_logons$ 
```

```
matthew@matthew-laptop:~/my_documents/my_logons$ file /bin/zsh4
/bin/zsh4: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped
matthew@matthew-laptop:~/my_documents/my_logons$
``` 

Neither of the above examples have file extensions.

Kind regards

---

### Post by MG&amp;TL on 2011-08-10
Thanks, matt_symes. If that's right, then why do C++ source code files have '.cxx' or '.h' appended to them?

Not putting you down, just intrigued. I will have to further examine my Xubuntu machine-it is not immune from weirdness.

---

### Post by CatKiller on 2011-08-10
Convenience. The same reason configuration files often end with .conf. File name extensions aren't generally needed, but they help the user know what the file is for.

---

### Post by matt_symes on 2011-08-10
Hi

> **MG&TL said:**
> Thanks, matt_symes. If that's right, then why do C++ source code files have '.cxx' or '.h' appended to them?

Not putting you down, just intrigued. I will have to further examine my Xubuntu machine-it is not immune from weirdness.

Just to expand on what CatKiller said;

A C++ file is just a text file. Just like a bash script is a text file.

Kind regards

---

