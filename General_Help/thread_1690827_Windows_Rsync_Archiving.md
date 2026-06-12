---
title: "Windows Rsync Archiving"
date: 2011-02-19
forum: General Help
---

### Post by ericdaviau on 2011-02-19
I have looked at most of the Back up posts and I still can't find my solution.  I am backing up may data using Rsync via SSH.  

I am trying to find a solution that allows me to push my backups from windows and Ubuntu to a Ubuntu server.  I don't like the solution that requires my windows machines to have shared drives. Not viable for laptop users that may piggyback on free wireless networks.

I would also like a solution that has a GUI for the desktop user but not totally required.  

I will need a solution that allows me to restore files by date.  I do a lot of changes to files on a daily basis and sometimes need an older copy of a file.  

I love using Rsync as it is a very simple solution and extremely quick.  The only thing I don't know how to do is recover different version of a file.  It would be nice to see a visual representation of all the files and different dates of each file. 

I know I might be asking a little too much, but, it is after all, Linux.

---

### Post by Wtower on 2011-02-19
Are you backing up your data from within a lan or the internet?

---

### Post by ericdaviau on 2011-02-19
I am currently doing this within my own lan.  I have to master this before I can do it securely across the internet.

My plan is to have all clients push their information via rsync via ssh and then backup the server to a second server.  I have had a disaster before and it is not nice.

I am able to push everything right now but once again, I can not retrieve multiple versions of the same file.  This is the crucial part.  And if this can be done through a client GUI, that would be awesome.  I looked at NASbackup but the installation instructions were very vague at the least.

What ever help I can get to accomplish this, I will put together and write up the entire instruction and post for others to use like I did for a Debian/OpenERP installation.

Thanks for responding Wtower!

---

