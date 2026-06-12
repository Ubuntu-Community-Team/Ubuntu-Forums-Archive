---
title: "Remote FTP Folder?"
date: 2011-06-11
forum: General Help
---

### Post by tripledot on 2011-06-11
To start off, I couldn't find a sub-forum which I thought fit this question well...

Anyhow, I am fairly new to programming, and I recently finished a project with a few guys.  During this project we were using SVN to save revisions to a remote server.  I really fell in love with this way to upload documents to a remote server via terminal.
I am currently working on developing the foundation of a website using PHP, and I was wondering if you could tell me how I would go abouts creating a folder on my desktop which would connect directly to a folder on my server?  This would be so I could easily edit the files in this folder, and when I save - the new modified data can be updated on the server.

I have only used FTP Clients with GUI's but they seem rather slow for rapidly modifying code, since you have to "drag and drop" and then agree to overwrite, etc.

Any suggestions will help!  Thanks.

---

### Post by Lars Noodén on 2011-06-11
My suggestion would be to look at SFTP instead.  It is built into OpenSSH Server.  Then you could connect to the remote folders using Nautilus, Dolphin or any number of regular [SFTP clients](http://en.wikibooks.org/wiki/OpenSSH/Client_Applications#GUI_Clients).  There is even SSHFS which uses SFTP to mount the remote directories as a subfolder on your system.

---

