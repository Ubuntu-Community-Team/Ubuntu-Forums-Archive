---
title: "Anyone know a good graphical scp utility?"
date: 2006-05-26
forum: General Help
---

### Post by morrin on 2006-05-26
Hi

I'm basically looking for something that works like Winscp on Windows. I need to tranfers files to and from a server. I had been happily working away for a long time using just scp until the systems administrators decided to impose a blanket policy of restricted shells(no "ls" or "cd"), which means I can't just ssh in now and traverse directories until I find what I need and then scp in or out.

However when using something like winscp , I can see the filesystem.I've been emailing them and trying to get them to revert back to the normal shell but they aren't gonna budge. So does anyone know of a client that would suit me. 

Thanks

---

### Post by detour on 2006-05-26
putty or gftp, maybe? Not sure if they rely on using ls...

---

### Post by Seq on 2006-05-26
Have you tried with Nautilus?

"sftp://remotehost/home/user"

---

### Post by morrin on 2006-05-26
Hey thanks. Nautilius works anyway. It's a bit unwieldy .... I'd rather just use a non-gui command line , but sure at least it'll get the job done8)

Hey actually, I've just realised I can connect with command-line sftp. I hadn't bothered trying that before. Is there any way that I can "break out" of the restricted shell i.e execute some remote commands ? Just curious. It would make my life easier if I could run , for example vi, to edit a few files on the remote machine rather than copying them back and forth

---

### Post by eldorel on 2006-05-30
Try this on for size, 
vim scp://user@host/path/to/file
or
vim [ftp://user@host/path/to/file](ftp://user@host/path/to/file)

either one will allow you to edit files without the Download/edit/Upload cycle....

---

