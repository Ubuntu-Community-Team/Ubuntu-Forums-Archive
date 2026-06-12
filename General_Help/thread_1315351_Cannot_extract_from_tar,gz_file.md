---
title: "Cannot extract from tar,gz file"
date: 2009-11-05
forum: General Help
---

### Post by milindras on 2009-11-05
Hi
I took a backup of home directory (cgi,home,public_html,logs) of a website which is hosted on one of my ubuntu server.
Lets say backup name domainame.co.uk.tar.gz
 
I need to restore this site to a different ubuntu server (testing). So when I tried to extract that the following error comes.
 
root@ns1:/home/phoenixleisure/public_html/test# tar xzf domainame.co.uk.tar.gz
tar: Skipping to next header
gzip: stdin: invalid compressed data--format violated
tar: Child returned status 1
tar: Error exit delayed from previous errors
 
I can see just some folder names extracted from the archieve but no files inside that.
 
Any advice?
 
Many Thanks

---

### Post by orasis on 2009-11-05
> **milindras said:**
> Hi
I took a backup of home directory (cgi,home,public_html,logs) of a website which is hosted on one of my ubuntu server.
Lets say backup name domainame.co.uk.tar.gz
 
I need to restore this site to a different ubuntu server (testing). So when I tried to extract that the following error comes.
 
root@ns1:/home/phoenixleisure/public_html/test# tar xzf domainame.co.uk.tar.gz
tar: Skipping to next header
gzip: stdin: invalid compressed data--format violated
tar: Child returned status 1
tar: Error exit delayed from previous errors
 
I can see just some folder names extracted from the archieve but no files inside that.
 
Any advice?
 
Many Thanks

1. It might need an extra command like -xvjf instead. 
2. It could be damaged. 
3. You might not have tarred the directory properly. 

But since it says invalid compressed data I hope for you it means add j (or another) switch rather than data corruption...

---

### Post by milindras on 2009-11-05
Thanks for the quick reply.
Please see below.
tar -xvjf phoenixleisure.co.uk.tar.gz
bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Error exit delayed from previous errors

Actually the backup I taken is done automatically through webmin. It creates a tar.gz file & ftp to a local machine.
Do you think its corrupted?
 
Thanks
 
Thanks

---

### Post by milindras on 2009-11-05
Hi,
I compraed the file sizes after upload to the server & I can see there is a difference between those.
So I Uploaded it again & this time it worked.
 
Thanks So much

---

