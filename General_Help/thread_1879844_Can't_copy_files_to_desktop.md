---
title: "Can't copy files to desktop"
date: 2011-11-12
forum: General Help
---

### Post by tech291083 on 2011-11-12
Hi,

I am using Ubuntu 10.10 and suddenly when I am trying to copy some files from the downloads directory to desktop it is not allowing me to do so. Even Firefox is not working. What could be the reason. The other OS on the same pc are working fine including Fedora. Thanks

---

### Post by ReptilianShadow on 2011-11-12
Just making sure, are the files listed in /home/{username}/Desktop folder of nautilus?
Perhaps the files are just placed awkwardly on the desktop? (out of screen view) 
Do the file names start with a period? (ex: .blah.mp3)

Just covering the bases of common "problems".

Do you get an error when you try to move them?

---

### Post by tech291083 on 2011-11-13
Hi,

I just realized that when I was trying to recover some deleted files as mentioned in my another thread, I typed a command after watching a YouTube video and since then I am having this strange problem. Here is the command that I ran.


```
sudo foremost -v -i /dev/sda8 -o /home/james/Desktop/DeletedFiles
```

This command started listed the deleted files one by one but it continued or more than 45 minute and then I stopped it midway. Please help me. Thanks.


Please have a look at these images. Thanks.

---

### Post by AlexDudko on 2011-11-13
Don't your screenshots tell you anything? You are simply short of disk space.

---

### Post by tech291083 on 2011-11-13
```

james@james-G31-M7-TE:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7             4.6G  2.9G  1.6G  65% /
none                  491M  264K  491M   1% /dev
none                  497M  188K  496M   1% /dev/shm
none                  497M   92K  497M   1% /var/run
none                  497M     0  497M   0% /var/lock
/dev/sda5             461M   30M  408M   7% /boot
/dev/sda8              28G   28G     0 100% /home

```

---

### Post by linuxwin2 on 2011-11-14
The last line tell that your /home is full (100%)

/dev/sda8              28G   28G     0 **100%** /home

And Desktop is a directory under /home/usename/

---

