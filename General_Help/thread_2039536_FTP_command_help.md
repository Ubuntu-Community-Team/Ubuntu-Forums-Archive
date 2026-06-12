---
title: "FTP command help"
date: 2012-08-09
forum: General Help
---

### Post by coolx on 2012-08-09
Hi,
There should be a command that enables upload and download files with a single line command. But I cant remember and couldnt be able to find. How can I do that?

Line should be something like that;

ftp 12.12.12.12 username password > file.txt

---

### Post by coolx on 2012-08-09
Any idea?

---

### Post by codemaniac on 2012-08-09
> **coolx said:**
> Hi,
There should be a command that enables upload and download files with a single line command. But I cant remember and couldnt be able to find. How can I do that?

Line should be something like that;

ftp 12.12.12.12 username password > file.txt

SFTP, or secure FTP, is a program that uses SSH to transfer files. Unlike standard FTP, it encrypts both commands and data, preventing passwords and sensitive information from being transmitted in the clear over the network. 

To start an SFTP session, at the command prompt, enter:

```
sftp username@host
```

PS : you need to use public key authentication for a passwordless login .

---

### Post by coolx on 2012-08-09
But I need to do only with FTP protocol.

---

### Post by steeldriver on 2012-08-09
I think you'd need to write a shell script - you could use a ~/.netrc file to auto connect, but afaik there's no direct way to pass the actual 'get' command on the ftp command line

---

### Post by codemaniac on 2012-08-09
> **coolx said:**
> But I need to do only with FTP protocol.

You requirement is still not clear , do you want to automate all the ftp operations from a shell script ?

If so you can write up a ftp script that will hold all the ftp commands and call the script from a shell script .

[http://www.stratigery.com/scripting.ftp.html](http://www.stratigery.com/scripting.ftp.html)

---

