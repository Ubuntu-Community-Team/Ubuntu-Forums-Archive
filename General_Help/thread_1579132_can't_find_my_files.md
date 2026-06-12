---
title: "can't find my files"
date: 2010-09-21
forum: General Help
---

### Post by diav1111 on 2010-09-21
I have a dual-boot system with windows and Ubuntu. In the partitioning  stage during the ubuntu install i created three partitions for ubuntu:  one partition / (28 GB),  one partition /home (10 GB) and one partition  /usr (10 GB). All my files were saved in /home/diav/downloads. 
Today  I formatted the partition / to reinstall ubuntu, but I didn't format  the partitions /home and /usr in order to keep my files safe. Now when I  use the disk utility, it shows me all the partitions, but the  partitions I didn't format mount at different names.
I mounted them  and i tried to find my files, but I can't. There is a folder named  "lost+found", which I can't open it. I think my files might be inside  it. When I try to open it, it shows me a message saying "The folder  contents cound not be displayed. You do not have the permissions  necessary to view the contents of "lost+found"". I don't know what i  have to do to open it. Do I have to log in as a root? And how i do that?  I have no idea how the terminal works.
Thank you in advance.

---

### Post by gnush on 2010-09-21
```

sudo cd /lost+found
ls -al

```

To enable the root account, which you shouldn't have to with sudo, you type the command I write below.

```

sudo passwd root

```


To search for files you can use the *locate *command.

```

locate -i filename
*The -i tells locate to ignore case *distinctions when matching patterns.

```

---

### Post by termin on 2010-09-21
also, if you cant find the file, then its most likely not updated. to update files go to  terminal and type:
sudo updatedb
and then do the locate command like the guy above me said

---

### Post by diav1111 on 2010-09-21
When I write sudo cd /lost+found it writes "sudo: cd: command not found".

---

### Post by WorMzy on 2010-09-21
Because cd is built into the shell you can't chain it with sudo. Instead, use:
```
sudo -i
cd /lost+found
```

Once you've cd'd to that folder, you can list the directory contents with```
ls
```

---

