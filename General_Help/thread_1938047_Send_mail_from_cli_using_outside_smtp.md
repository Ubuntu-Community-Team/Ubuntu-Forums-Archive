---
title: "Send mail from cli using outside smtp"
date: 2012-03-09
forum: General Help
---

### Post by Ghost_Mazal on 2012-03-09
Lo all ,

Wasn't sure where to post this. I have searched but couldn't find an answer.

My situation :

I have an 11.10 server on my lan. I need to send a .txt file from that server via email. However there is no mta installed on the server. The server does not have access to internet so that I can apt-get anything. The server does see a mail server on the lan though that I can use as an smtp. 
I need a command that can send a txt file via mail using that other smtp server on the lan network. Can this be done ?

Any help will be appreciated thanx.

---

### Post by wojox on 2012-03-09
If you have ssh installed you could always use Secure Copy:

This is the Linux scp command syntax to send file or directory to a remote computer:

```
scp -r [/path/filename] [login name@ip address] : .
```

This is the Linux scp command syntax to retrieve file or directory from a remote computer:

```
scp -r [login name@ip address] : [/path/filename] .
```

---

### Post by Ghost_Mazal on 2012-03-09
> **wojox said:**
> If you have ssh installed you could always use Secure Copy:
 
This is the Linux scp command syntax to send file or directory to a remote computer:
 
```
scp -r [/path/filename] [login name@ip address] : .
```
 
This is the Linux scp command syntax to retrieve file or directory from a remote computer:
 
```
scp -r [login name@ip address] : [/path/filename] .
```
 
That's not what I need exactly.
 
Let me give some more info. I need to get my ubuntu server's disk usage every day.
But I need to get it via my email because I will forget to check the file manually.
 
But my email is on a different server. So I need that ubuntu server to email me the disk usage report (which already runs to a simple text file) , but using the working smtp on the network as the ubuntu server itself has no mta installed. And it must be cli so that I can add it into a scrypt for automation

---

### Post by lisati on 2012-03-09
It sound like something similar to [Mutt]("https://help.ubuntu.com/community/mutt") might be useful.

---

### Post by Ghost_Mazal on 2012-03-09
I see now that Postfix is in fact installed on my ubuntu server. But I have no idea how to configure it.

---

### Post by Ghost_Mazal on 2012-03-09
Yay , got it working :)
 
Thanx guys
 
First I did:
 
```
 
sudo dpkg-reconfigure postfix

```
 
And added the smtp in the relay option
 
And then run:
 
```
 
df -h | mail -s "Disk usage" [EMAIL="me@my.adress"]me@my.adress[/EMAIL]

```

---

