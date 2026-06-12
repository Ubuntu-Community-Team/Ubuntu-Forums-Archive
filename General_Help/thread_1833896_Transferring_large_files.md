---
title: "Transferring large files"
date: 2011-08-26
forum: General Help
---

### Post by Mark_in_Hollywood on 2011-08-26
NOT REALLY AN UBUNTU QUESTION. But if you want to read further and help, it is appreciated.

I recorded a PBS TV show. It's about 10.8 gig. I want to send it to a friend several hundred miles away. I know there are file-hosting-sharing websites, but which one is good-better-best for Ubuntu?

---

### Post by hasardeur on 2011-08-26
10.8GB is a lot of data. I would suggest, that you avoid a web hosting service. Share the file via ftp. Either you create a ftp server or your friend and you copy the file directly. You could also sample the recording down, so uploading to a hoster would be easier.

---

### Post by Mark_in_Hollywood on 2011-08-26
OK - no file sharing but where do I get a server for a FTP?

---

### Post by hasardeur on 2011-08-26
Don't get me wrong, share all you want! I am a strong supporter of the freedom of information. But in this case it is just not that practical. To install the FTP server on your machine read this: 

[http://ubuntuforums.org/showthread.php?t=79588&highlight=ftp+server+howto]("http://ubuntuforums.org/showthread.php?t=79588&highlight=ftp+server+howto")

OR: Your friend can install the server and you simply connect to the server with a client and start the transfer. Installing the client is as easy as

```
sudo apt-get install filezilla
```

---

### Post by Mark_in_Hollywood on 2011-08-26
Sorry to say, friend uses Windows. Any freeware for FTP there?

---

### Post by wannabegeek on 2011-08-26
Skype  has a share files tool....never tried it...back in the day I remember having a friend call my modem to transfer files....

---

### Post by artantaaa on 2011-08-27
Most instant messengers will let you transfer files back and forth. I've used pidgin and other programs to send stuff to someone on yahoo before.

---

### Post by dcstar on 2011-08-27
> **hasardeur said:**
> 10.8GB is a lot of data. I would suggest, that you avoid a web hosting service. Share the file via ftp. Either you create a ftp server or your friend and you copy the file directly. You could also sample the recording down, so uploading to a hoster would be easier.

Don't recommend a specific Ubuntu distro, by the time this 10+GB is uploaded chances are the next Ubuntu release will have come and gone.... ;-)

---

