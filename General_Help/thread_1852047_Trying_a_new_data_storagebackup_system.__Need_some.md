---
title: "Trying a new data storage/backup system.  Need some advice."
date: 2011-09-29
forum: General Help
---

### Post by ninjaaron on 2011-09-29
Ok.  I bought a new external HDD today for data storage.  I bought it specifically for storing things like documents (including many PDFs and Ebooks), music, and video, as an archive.  I'd like to be able to transfer data from it to a variety of other systems, including my friend's OSX and Windows machines.  I'm thinking about NTFS for portability at the moment, but I really want something journaled for a drive of this size, especially as there are no defragmenting tools for Linux (as far as I know).  If there is a possibility for that, it would be preferable.

The other device is 320GB for backing up my home folder and other places where settings are stored (such as /usr/share and /etc).  For this, I'm probably going to use ext4, like I do for everything else.  I'll probably use rsync or some derivative thereof for this.  I'm also curious if there is anything else I ought to back up besides /home, /usr/share and /etc.

---

### Post by papibe on 2011-10-05
Hey ninjaaron,

I do full backups of my /home partition, but I also backup configuring files all over my system. Every time I modify a file, I create a copy with a special 'extension'. For example, when I supersede the DNS servers on my DHCP client configuration:
```
$ sudo cp /etc/dhcp3/dhclient.conf /etc/dhcp3/dhclient.conf.oldback
```
When is time to backup, I have a script that look for '*.oldback' files in my system. When found, I backup the copy and the original file.

Kind Regards.

---

