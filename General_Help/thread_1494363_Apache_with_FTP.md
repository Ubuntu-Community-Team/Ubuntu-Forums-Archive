---
title: "Apache with FTP"
date: 2010-05-26
forum: General Help
---

### Post by Karhan on 2010-05-26
I've set up an apache web server to run a few php sites which will be located in the user's home directories (/home/username/) and using virtualhost configuration files to redirect traffic to the appropriate locations but now I'm having some issues I guess with permissions. 

when I ftp files into my home directory and view them in the browser (php files specifically) they complain of permission issues while trying to access some libraries in the filesystem. I found that if I chmod 755 the directory these issues go away but that those changes wont apply to new files I upload. 

the only thing I'm sure about is that I'm 'doin it wrong' and my hope is that someone here can at least point me in the right direction. 

I really appreciate any and all responses in advance. 

Thank you!

---

