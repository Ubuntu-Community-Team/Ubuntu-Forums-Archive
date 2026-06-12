---
title: "timestamping using wget"
date: 2010-01-18
forum: General Help
---

### Post by 7raTEYdCql on 2010-01-18
I'm trying to sync some files present on an ftp server to my personal computer. For this i am using wget.
The command goes as follows: wget -Nr remote-url 

New files which are added on the ftp server will get downloaded onto my computer, but what about files which are later deleted from the server. Will that be deleted from my comp as well. From what i've understood, wget only checks the timestamps from my directory listing(for ftp) and finds for newer files on the server.

Can someone please help.

---

### Post by falconindy on 2010-01-18
Sounds like you're trying to sync two locations. Use sftp via rsync instead.

---

### Post by 7raTEYdCql on 2010-01-18
hmm... i read about it, not comfortable with the syntax. I'll check it out though. Thanks, but then my method still works. BTW, does rsync delete the files from my local machine, which have been removed from the ftp server??

---

### Post by falconindy on 2010-01-18
> **i.mehrzad said:**
> hmm... i read about it, not comfortable with the syntax. I'll check it out though. Thanks, but then my method still works. BTW, does rsync delete the files from my local machine, which have been removed from the ftp server??
Yes, it will. Use the --delete flag.

Basic execution of rsync isn't hard at all. It's the same as any file manipulation command:

rsync [options] <source> <destination>

---

### Post by 7raTEYdCql on 2010-01-18
I've written the script(using wget), how do i get the script to periodically check for updates.

---

### Post by falconindy on 2010-01-18
Use cron.

---

