---
title: "ftp upload problem"
date: 2009-11-26
forum: General Help
---

### Post by stavropd on 2009-11-26
Hello,

 I have a problem when trying to upload (ftp) a file to a specific server. 
 In detail, I have 6 PCs with Ubuntu 8.10 that are on the internet with different IPs. One of the machines is the server that I use to upload and download files using the rest of the machines. 
 
I am able to upload files properly from the rest 4 PCs but this specific PC (the 5th) cannot upload files on my server. However, the ftp upload process seems to work fine for every other ftp server. And the thing is that this problem just started a day ago. Before yesterday this PC was working fine. 
 
For the ftp, I use the CLI:
ftp>open "hostname"
ftp> put "file" ,when connected with the server.
200 PORT command successful. Consider using PASV.
150 Ok to send data.
 
And I am stuck there.
I can see the "file" created at the servers side, but it is an empty file (0 kb).
 
Is there anyone who can help with the above problem? Thanks

---

