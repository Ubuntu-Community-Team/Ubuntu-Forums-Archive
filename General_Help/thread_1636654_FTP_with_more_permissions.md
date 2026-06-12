---
title: "FTP with more permissions"
date: 2010-12-03
forum: General Help
---

### Post by daj_uk on 2010-12-03
Sorry if this is a really basic question, but I have been reading online help all afternoon, and it has really helped me on setting up virtual hosts but this one confuses me.

I appreciate that 'root' is not enabled for login and the recommendation is that it should not be.  I also understand sudo to elevate myself to root equivalent to do admin tasks.

However, I would like to use an FTP client to edit some of the files on the server but sudo obviously does not work.

At the moment I have to use sudo vi <filename>   I would really like to FTP onto the server, download the file, edit it and re-upload it. However as an FTP user I do not have write permission to the files.

Is this possible?

I'm using Ubuntu 10.10 server

Many thanks

David

---

### Post by galvatron408 on 2010-12-03
You can't do that with FTP. FTP is for file transfer purposes only. For editing, use ssh.

just type "ssh yourserver"

---

### Post by daj_uk on 2010-12-03
yes, I appreciate what FTP is for -- I want to transfer the file, work on it on my PC, then transfer it back up.  I just do not have sufficient permissions to save it back to the server as I am not root.

I already use SSH and then vi the file, but vi is not nice when you are editing several lines of text

---

### Post by Slim Odds on 2010-12-03
> **daj_uk said:**
> yes, I appreciate what FTP is for -- I want to transfer the file, work on it on my PC, then transfer it back up.  I just do not have sufficient permissions to save it back to the server as I am not root.

I already use SSH and then vi the file, but vi is not nice when you are editing several lines of text

Why not? I've had no problems with it.

You can also use any other programs that you like via ssh.

---

### Post by drdos2006 on 2010-12-03
I use Webmin to control my home server and vsftp to upload and download files to my server. Vsftp is very simple to set up.
Filezilla is the client on my workstations.


regards

---

