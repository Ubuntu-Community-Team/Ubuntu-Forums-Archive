---
title: "Unusual disk space usage"
date: 2010-03-22
forum: General Help
---

### Post by iption on 2010-03-22
I just did a fresh install of karmic koala x64 version. The thing that surprised me is the disk usage. It uses 6.2 GB of the disk. (My home is only ~250Mb).
I emptied root trash and lost and found and is still that big. I checked with root and all the files combined have 3.1 GB, but the usage is double. Any idea how to reduce this?

---

### Post by cjhabs on 2010-03-22
> **iption said:**
> I just did a fresh install of karmic koala x64 version. The thing that surprised me is the disk usage. It uses 6.2 GB of the disk. (My home is only ~250Mb).
I emptied root trash and lost and found and is still that big. I checked with root and all the files combined have 3.1 GB, but the usage is double. Any idea how to reduce this?

How are you checking these sizes?

---

### Post by drs305 on 2010-03-22
I haven't run into this in quite some time. This used to be a problem with  Disk Usage Analyzer. If .gvfs is included in the total it can show double the actual disk usage. Additionally, DUA includes the results from all mounted partitions, so you might want to unmount any extra drives you have that may alter the reposrted size of /.


If you run the following two commands after closing your open apps you should get an accurate result:
```
sudo umount -a  # Unmounts non-system partitions not in use. You will get "Busy" messages - that's ok.
df -Th
```

The "DiskSpace" link in my signature line includes lots of ways to determine how much space you have and what might be taking it up.

---

### Post by iption on 2010-03-22
I did unmount everything, otherwise the disks in /media would show.
I did check that link before and did all that cleaning but it didn't help.
As for the checking, I used Disk Usage Analyzer which says that i have used 6.2 GB but folders below added up show only 3.1 GB. Also Nautilus - all files selected -> properties show 3.1 GB combined, but freespace is only 500 mb I think (not what it should be). 
And also when I installed something it said I have a low disk space.

---

### Post by cjhabs on 2010-03-22
> **iption said:**
> I did unmount everything, otherwise the disks in /media would show.
I did check that link before and did all that cleaning but it didn't help.
As for the checking, I used Disk Usage Analyzer which says that i have used 6.2 GB but folders below added up show only 3.1 GB. Also Nautilus - all files selected -> properties show 3.1 GB combined, but freespace is only 500 mb I think (not what it should be). 
And also when I installed something it said I have a low disk space.

I hadn't used disk usage analyzer before - I tried it and it appears to be completely incorrect. I will stick to "df -k" and "du -k -s".

---

### Post by 2hot6ft2 on 2010-03-22
> **cjhabs said:**
> it appears to be completely incorrect. I will stick to "df -k" and "du -k -s".
+1
and df -h
I disabled the Disk Usage Analyzer in gconf-editor by following this:

 > Originally Posted by SecretCode  View Post
While trying to solve this for myself I came across your post. And this is the solution:

Open gconf-editor (type gconf-editor at the command line), and navigate to the key /apps/gnome_settings_daemon/plugins/housekeeping/.

Double-click the ignore paths name, and remove the paths you want not to ignore any more.

There are some other useful configuration settings here, like free_percent_notify (default 0.05 meaning notify when space is less than 5%) and free_size_gb_no_notify (default 2 meaning don't notify if the free space is more than 2GB).

---

### Post by iption on 2010-03-23
I found out what the problem was. After I ran the Disk Usage Analiser under sudo i saw that the /root was 3.1 GB I don't know why sudo nautilus showed the folder was only a few KB, and when I deleted /root/.local/share/Trash/files the size was reduced.
Anyway thanks for the help. 
Does someone know how to make nautilus show the size of the subdirectories that are hidden, so this does not happen again?

---

