---
title: "How to edit a remote file securely"
date: 2006-04-25
forum: General Help
---

### Post by jazzmuzik on 2006-04-25
I would like to edit an html file on a remote server in a secure way, possibly over an ssh connection. Is this possible? For example, I know Bluefish can open and save a remote file, but is it secure? I'd like my local copy of Bluefish to open the remote file as if it were a local file. And then when I save the edited file there's no problem.

---

### Post by Ensnared on 2006-04-25
If you have an editor that supports sftp (e.g. ftp over ssh) then it's possible.

I personally use jEdit, which has a plugin that supports both regular ftp and sftp, but I don't know if Bluefish supports this.

Optionally you can securely copy the file to your local drive, edit it, then secure copy it back. That's fairly impractical though, but it will work.

To copy it to the current dir:```
scp -l username remote_host:/full/path/to/file.html .
```
To copy it back:```
scp -l username file.html remote_host:/full/path/to/location/
```

If your local username and remote username is the same, you can ignore the "-l username" part.

---

### Post by fheinsen on 2006-04-25
[quote=jazzmuzik]I would like to edit an html file on a remote server in a secure way, possibly over an ssh connection. Is this possible? For example, I know Bluefish can open and save a remote file, but is it secure? I'd like my local copy of Bluefish to open the remote file as if it were a local file. And then when I save the edited file there's no problem.[/quote]

Another way for you to do this is with the SSH file system, or SSHFS, which would allow you to mount remote volumes over SSH and then access them from virtually any application as if they were local.   Here's a good how-to:

[http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-%20%20filesystem-using-sshfs/](http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-%20%20filesystem-using-sshfs/)

---

### Post by Ensnared on 2006-04-25
Just checked the [Bluefish manual](http://bluefish.openoffice.nl/manual/ch03s03.html#remote-files) and according to that, you should be able to access remote files using the sftp.

I just installed Bluefish on my Breezy-box, and checked how it works - and it does :)

Go to File->Open URL
Enter "sftp://remote_host/path/to/file"
Or, if you have to specify a different username: "sftp://username@remote_host/path/to/file"

You'll then be prompted to accept the remote key, and for your password. The file can be a dir - you'll get an error saying file not found, but the remove system will now be browseable in the location sidebar in Bluefish :)

---

### Post by jazzmuzik on 2006-04-25
Cool. I've got multiple methods. I tried sshfs and it works well. Thanks for the help.

---

