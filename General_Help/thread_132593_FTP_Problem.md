---
title: "FTP Problem"
date: 2006-02-18
forum: General Help
---

### Post by Ingla on 2006-02-18
Hello.

I'm having a problem with gftp. I can access my sites, upload, download and delete files OK. 

However, when I try to rename a file (which I do often), I get "permission denied". I have to go to Windows to make the change. 

Does anybody know what I can do about this?

Thanks.

---

### Post by nalmeth on 2006-02-18
Probably little you can do. It probably has to do with windows ntfs filesystem, which will only allow windows to modify the filesystem. You are talking about renaming files on the windows partition right?

---

### Post by Ingla on 2006-02-18
Hi.

Thanks for the reply.

I'm talking about renaming files on my web site, which is hosted on a windows server.

---

### Post by knalle on 2006-02-18
then it sounds like that windows ftp server needs som config because gftp is working against the straight FTP  protcol and gftp isn't broken as far as i know

---

### Post by Ingla on 2006-02-18
Thanks.

What does that mean for me? Can I do anything? Should I ask my host's support to make things work?

---

### Post by knalle on 2006-02-18
if you are sure that you are using gftp right then you should talk to the windows server BOFH about it.

You might have to sett the permissions of a file before you can rename it, select it and change the permission so you can write to the file

---

### Post by Ingla on 2006-02-18
Still not sure what you mean. File permissions are set by the hosting company, unless I do something in their control panel to make it password protected.

These files are not on my machine.

Please advise.

Thanks.

---

### Post by knalle on 2006-02-18
no, no, inside gftp, while connected to the windows host, select the file and set permissions

---

### Post by Ingla on 2006-02-18
Sorry...still don't quite get it. I don't see any way to change permissions in gftp.
Right click on the folder (that's what I'm trying to rename) doesn't show such an option.

How do I do it?

Thanks.

---

### Post by knalle on 2006-02-18
right click on the folder and select "chmod", **chmod** means permission in linux speak.

---

### Post by Ingla on 2006-02-18
I already have read and write permissions for user, group and other. There's also an "execute" permission which is unchecked, but I don't want to execute anything.

What do you think?

---

### Post by knalle on 2006-02-18
execute has a special meaning for folders in linux, execute means if people can look into the folder or not. shouldn't matter but try to set all to read|write|execute.

are you sure you own the folder? see under 'user'

---

### Post by Ingla on 2006-02-18
I can't find any user name. I must own the folder because I created it and uploaded all contents. I opened the folder and can see everything (without changing the permissions to allow execute). 

This doesn't happen under Windows. I can do anything I want accessing with only my ftp or IP address and password...?

---

### Post by knalle on 2006-02-18
[QUOTE=Ingla]This doesn't happen under Windows. I can do anything I want accessing with only my ftp or IP address and password...?[/QUOTE]

which ftp program do you use under windows?

---

### Post by Ingla on 2006-02-18
Usually FTP Surfer.

---

### Post by knalle on 2006-02-18
and you are able to rename the file with ftpsurfer?

---

### Post by Ingla on 2006-02-18
Yes, when I couldn't do it with gftp, I went to Windows and did it.

---

### Post by knalle on 2006-02-18
yes, but did you do it with windows file manager or ftpsurfer?

---

### Post by Ingla on 2006-02-18
I did it with FTP surfer.

By the way gftp does everything else I've tried...upload, download and delete.

---

### Post by knalle on 2006-02-18
sounds very strange, perhaps gftp is broken, i don't use it myself, you could try 
[B]
sudo apt-get install kbear[/B]

**kbear** is a kde ftp client, see if that one works for you

---

### Post by Ingla on 2006-02-18
I installed kbear with Synaptic. It looks nice and accessed my site without difficulty. However, it contains no help files and I can't find any commands for rename. Also, there are two frames, but they both show either my local file system or my site, but not both. 

I don't see any way to upload, download or rename...just delete.

How can I get help on this?

---

