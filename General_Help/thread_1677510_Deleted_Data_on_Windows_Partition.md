---
title: "Deleted Data on Windows Partition"
date: 2011-01-28
forum: General Help
---

### Post by Odzinic on 2011-01-28
Hello all
I just made a very stupid mistake, and in result I just deleted almost everything on my windows 7 partition. 
I followed this guide: [http://technical-itch.co.uk/2006/11/06/how-to-access-your-windows-hard-drive-from-ubuntu/](http://technical-itch.co.uk/2006/11/06/how-to-access-your-windows-hard-drive-from-ubuntu/) for how to access my windows partition from ubuntu and it worked, but then I decided to rm -r the whole thing thinking it was a copy. I have no restore disks or any other type of backup. I know this maybe be impossible, but is there any way to recover my data?

Thanks.

---

### Post by oldfred on 2011-01-28
Not sure how rm deletes things. 

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
Maverick the software sources is System, Administration, Update Manager, settings button on lower left.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

But I think since each file was deleted you will have to use photorec or similar software to recover files. You will not be able to recover a bootable system. And the files recovered have no names, just numbers and extensions.

Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
How to recover lost files after you accidentally wipe your hard drive
[http://www.linux.com/archive/feed/56588](http://www.linux.com/archive/feed/56588)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)

gddrescue, Scalpel, magic rescue, photorec, foremost, sleuthkit & others
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

I use photorec to recover some data and a textfile that I had save many times was recovered many times. Between backup and some of the files I recovered most of my textfile but I had so many versions, I was not sure I had ever found the last saved version.

---

