---
title: "Multiple File Upload Socket Error"
date: 2010-01-24
forum: General Help
---

### Post by lives4him06 on 2010-01-24
Hello all,
I am pragmatically trying to upload a list of files from my client machine to a proFTPd server I have running on Ubuntu. Every time I get several (around fifty) files into the transfer, I get the following error:

> Connection reset by peer: socket write error

Am I using up all available sockets before they can be released? If so, how do I release the sockets? If not, what does this error mean and why am I getting it?

---

### Post by Lucid Smog on 2010-01-24
This could be caused by your client.  Is this an FTP client that you wrote or something else?  With the information at hand it is very difficult to determine what the issue might be.  It is possible that your client is issuing many PORT commands and not closing them properly and thus the server is refused to allocate more socket descriptors, but it seems unlikely.

Have you looked in the proFTPd server logs or /var/log/messages to see if there are any errors in there?

Alternatively, install vsftpd and see if it doesn't give you the problem.

---

### Post by lives4him06 on 2010-01-24
Im almost certain this problem is caused by the client as I have already tried vsftpd with the same error.

I have implemented edtftpj with java to write my own client, so I'd bet I'm not closing something correctly, but Id love some pointers if you have them. 

What would I look for in /var/log/messages?

---

### Post by lives4him06 on 2010-01-31
Update:

I am able to remotely upload 25,000 small files of ~ 1K in size, but when I go to upload hundreds of 2-4 Mb files, I get a socket write error.

Can anyone explain why this is happening?

---

### Post by lives4him06 on 2010-02-25
Though I am still receiving this error, I have built some controls into my code to mitigate it's effects. I think it is my ISP (Comcast) that is causing this as I have changed routers, changed FTP servers, and changed Java FTP librarys I have used in my code.

---

