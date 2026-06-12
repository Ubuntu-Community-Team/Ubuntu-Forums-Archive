---
title: "SFTP Directory Restriction"
date: 2010-06-14
forum: General Help
---

### Post by bbergkamp on 2010-06-14
I am setting up an SFTP server with Openssh and I have a few quick questions.

I need to restrict access of each user to only one directory.  Right now each user can brows up directories and see pretty much everything on the server. I have looked at other forum posts and none have an explicit answer.  I was thinking I could remove all file permissions for the user and then add rw access to only the directory I choose. 

I am used to FTP where I would give users access to just one directory, but with openssh all of the directories are viewable open by default.

Is removing all permissions and then adding one directory the best way to do this?
What would be the exact chmod commands to execute this for just one user?

---

### Post by Chesamo on 2010-06-14
Hm... SFTP isn't really what you want for this, if you want to restrict the user to one directory.

---

### Post by bbergkamp on 2010-06-14
What should I use instead?

I need to have access to my work files from anywhere so I am setting up a server.  I don't like that FTP doesn't send login information securely so I was thinking SFTP would be an alternative.

---

### Post by bbergkamp on 2010-06-15
What would the exact chmod commands be if the user was 'files'?

---

### Post by Chesamo on 2010-06-15
SFTP is a lot slower than FTP, because it has to handle the CPU overhead. FTP has no such restriction. If you're setting up this server for the sole purpose of transferring files, use [FTPS](http://en.wikipedia.org/wiki/FTPS).

In response to your question, the commands would be ```
sudo chmod -R o-rwx /home
sudo chmod -R uo+rw /home/files
``` If the user 'files' tried to navigate up from their home directory, they would be denied because they do not have Read permissions in /home.

---

### Post by bbergkamp on 2010-06-15
Thank you, this is very helpful.

I am looking into FTPS as well.  I tested my transfer speed with SFTP and it was fast enough.

How does chmod know which user to restrict assess to?  Do I log in as files before I run chmod?

---

