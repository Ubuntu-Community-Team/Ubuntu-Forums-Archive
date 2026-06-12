---
title: "[gparted] can't resize/move linux to fill unallocated space-- even from live cd"
date: 2012-09-28
forum: General Help
---

### Post by isa.dsouza on 2012-09-28
Thank you for the details [here: [http://ubuntuforums.org/showthread.php?p=12265668]](http://ubuntuforums.org/showthread.php?p=12265668])  I have successfully increased disk space for Ubuntu 12.04.1 LTS now. It did take some time but just 10 mins around about.

I dont know exactly but for some reason in System Monitor it shows that Total Disk Space is 47.5Gb, Free space is 41.9Gb, but Available Disk Space is 39.5Gb. The Used Space is 5.6Gb there is an unaccounted 2.4Gb, anyone know what to do?

I include a screenshot for a better understanding, of my question.

---

### Post by oldos2er on 2012-09-28
Post moved to its own thread.

---

### Post by spjackson on 2012-09-28
By default 5% of the filesystem is reserved. The reserved blocks are not counted in either used or free. Normally you would not change this. If you really need to, then [tune2fs]("http://manpages.ubuntu.com/manpages//precise/man8/tune2fs.8.html") is the tool.

---

### Post by Starcruiser322 on 2012-09-28
Also check how much swap space is allocated. Mine had an unnecessary 6 GB for a max space usage of 56K

---

### Post by isa.dsouza on 2012-09-28
Thank you for the answers. Ive done the math on the reserved space bit. It checks out alright.  

Learning all the time here. :)

While trying to search for missing files & other stuff though I tried 

sudo find / -size +50M

and get errors like so:

find: `/home/isa/.gvfs': Permission denied
find: `/proc/4136/task/4136/fd/5': No such file or directory
find: `/proc/4136/task/4136/fdinfo/5': No such file or directory
find: `/proc/4136/fd/5': No such file or directory
find: `/proc/4136/fdinfo/5': No such file or directory

logically this means there is a file that is > 50Mb n the folder so why cant I get into it inspite of running it as root?

is this a sign of some hacking?:(

---

### Post by oldfred on 2012-09-28
I just ran your command.

I get the same errors as certain files are not readable as they are mounted and locked.

The only files my system found were many ISO that I have downloaded (time to houseclean :) ), a movie of my Son's wedding, some photos I had scanned that became huge files, my Thunderbird mailboxes, and my Picasa databases. No system files came up as that large.

---

