---
title: "Looking for decent FTP program"
date: 2010-05-20
forum: General Help
---

### Post by Alan McNea on 2010-05-20
I am looking for a Ubuntu program to take the place of the windows application WinSCP.  What I am looking for is the following:

1) Able to handle FTP and SSH (SFTP)
2) Able to have an explore view for the remote file system. (Directory Structure on left, files on right, and no local files).
3) Able to edit files and auto update them on saving the file (not on closing gedit).
4) Able to edit files without being prompted every time an edit is saved/uploaded.
5) Works reasonably well on slow connections.

So far I have tried sshfs, gftp, and filezilla.

sshfs satisfies (1-4) but becomes unbearable on slow connections, but works great over a local network.

gftp satisfies 1, and 5.

filezilla satisfies 1, 3, 5.

If anyone out there knows a program which satisfies all 5 of my requirements or knows hows to configure the stated programs into meeting my requirements I would be most appreciative.  Also, I can live without requirement #2 if the other 4 are met.  Anyways, thanks in advance for any help you can give.

---

### Post by dino99 on 2010-05-20
[http://ubuntuforums.org/showthread.php?t=973431](http://ubuntuforums.org/showthread.php?t=973431)

have you checked proftp or vsftp ?

---

### Post by bodhi.zazen on 2010-05-20
> **Alan McNea said:**
> I am looking for a Ubuntu program to take the place of the windows application WinSCP.  What I am looking for is the following:

1) Able to handle FTP and SSH (SFTP)
2) Able to have an explore view for the remote file system. (Directory Structure on left, files on right, and no local files).
3) Able to edit files and auto update them on saving the file (not on closing gedit).
4) Able to edit files without being prompted every time an edit is saved/uploaded.
5) Works reasonably well on slow connections.

So far I have tried sshfs, gftp, and filezilla.

sshfs satisfies (1-4) but becomes unbearable on slow connections, but works great over a local network.

gftp satisfies 1, and 5.

filezilla satisfies 1, 3, 5.

If anyone out there knows a program which satisfies all 5 of my requirements or knows hows to configure the stated programs into meeting my requirements I would be most appreciative.  Also, I can live without requirement #2 if the other 4 are met.  Anyways, thanks in advance for any help you can give.

If you are happy with WinSCP you can probably run it with wine.

---

### Post by Vaphell on 2010-05-20
why don't you try to use nautilus for that? just type sftp://... in the location bar 
i do exactly that - i edit stuff on a remote server via ssh/sftp, but it looks just like local operations, i can browse as usual, ctrl+s in gedit updates files on remote server, no prompts except when you try to save but the file was modified by someone else.

---

