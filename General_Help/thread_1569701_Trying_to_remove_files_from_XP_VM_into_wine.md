---
title: "Trying to remove files from XP VM into wine"
date: 2010-09-07
forum: General Help
---

### Post by SpyderMars on 2010-09-07
I'm trying to move a file into Ubuntu from a virtual machine I made("Windows XP) but I can't seem to find a way to transfer that file. It wont read flash drives and I'm having a rather difficult time setting up a shared file.  I've flipped through a couple of articles, but didn't find anything that could help. 

A couple of examples:

[http://news.softpedia.com/news/How-to-Fix-VirtualBox-USB-Support-111715.shtml](http://news.softpedia.com/news/How-to-Fix-VirtualBox-USB-Support-111715.shtml)
[https://help.ubuntu.com/community/VirtualBox/SharedFolders](https://help.ubuntu.com/community/VirtualBox/SharedFolders)

Can anyone point the way onto more info regarding virtualbox?

---

### Post by garikaib on 2010-09-07
Move the file into the public folder under your home directory. Right click the folder and select share. Ubuntu should offer to download samba and configure it for you. After the download and configuration is complete boot into your virtual machine and got to my network places/network sharing center depending on the version of windows you are using. If you can see the shared folders just navigate to the one you want and copy the file(s) into your Documents folder. If this does not work and you don't see any folders at all just try typing \\the.host.ip in the Explorer address bar of your virtual machine replacing the.host.ip with the ip address of the machine running ubuntu. If this does not work also it might mean that your virtual machine's network settings are not set correctly and you need to look into this on the net. Also if the autoconfiguration of Samba does not work you might need to delve into the samba.conf file and configure manually. A good tutorial can be found on the Ubuntu wiki.

---

### Post by zvacet on 2010-09-07
Other option (when you already made shared folder) is [http://ubuntuforums.org/showthread.php?t=1055075&highlight=shared+folder+windows+guest&page=2](http://ubuntuforums.org/showthread.php?t=1055075&highlight=shared+folder+windows+guest&page=2) #14

---

### Post by zvacet on 2010-09-07
Other way to do that is described on [http://ubuntuforums.org/showthread.php?t=1055075&highlight=shared+folder+windows+guest&page=2](http://ubuntuforums.org/showthread.php?t=1055075&highlight=shared+folder+windows+guest&page=2) #14


Sorry for double post.

---

### Post by SpyderMars on 2010-09-09
> Other way to do that is described on [http://ubuntuforums.org/showthread.p...s+guest&page=2]("http://ubuntuforums.org/showthread.php?t=1055075&highlight=shared+folder+windows+guest&page=2") #14


Sorry for double post.I went looking through that post and ended up going with filezilla instead. I'll probably look more into the "shared folders" tho since I'm probably going to be using VirtualBox more often. Thank you for your help

---

