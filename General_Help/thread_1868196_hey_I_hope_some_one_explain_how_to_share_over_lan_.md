---
title: "hey I hope some one explain how to share over lan In ubuntu ?"
date: 2011-10-23
forum: General Help
---

### Post by Elshentenawy on 2011-10-23
hey guys 
I'm anew ubuntu user 
actually I have a wired network and when I was using windows I was using file share pro ..to share To all my network users 
I was asking is there any program look like file share pro which is sharing as a site ?

thanQ

---

### Post by oldtimer7777 on 2011-10-23
> **Elshentenawy said:**
> hey guys 
I'm anew ubuntu user 
actually I have a wired network and when I was using windows I was using file share pro ..to share To all my network users 
I was asking is there any program look like file share pro which is sharing as a site ?

thanQ

It is called Samba:

[http://www.linuxquestions.org/linux/answers/Networking/Basic_Samba_Network_File_Sharing](http://www.linuxquestions.org/linux/answers/Networking/Basic_Samba_Network_File_Sharing)

---

### Post by nickleboyblue on 2011-10-23
To use Samba:  right-click on a file, select "sharing options," and enable sharing in the dialog that pops up.  If you don't have samba installed at that point, it will ask you if you want to install that service.

Otherwise, if you're feeling ultra geeky, you could do it through sftp in the command line or inside of nautilus.  In that case, you could literally edit documents on one computer from an editor of your choice on another computer.  I've even watched movies that I stored on one machine and watched from another (one machine had a large HDD, the other had a television screen and 5.1 surround sound).

Sftp is a little more technical to set up, but it does a lot more than simple file copying.

Also, in order to access a samba file share from another Ubuntu machine using Unity, click on the "go" menu in the top bar of a desktop with no windows open on it and select "network".  At that point, you'll have to navigate to the sharing computer, at which point the share will show up and you can access it according to the settings of that particular file share (usually it's read-only, but you can also copy files TO the other computer).

---

