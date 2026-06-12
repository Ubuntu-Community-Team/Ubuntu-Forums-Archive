---
title: "umask help - not sure how to di this"
date: 2010-03-13
forum: General Help
---

### Post by hellsgate1001 on 2010-03-13
Hey folks,

I've set up LAMP on my Hardy installation. I've created an index.html in the www root. I created that file through ftp using my text editor (EditPlus - I'm working from a W*****s machine :) ). the file was created with 600 permissions, so to be able to view it in my browser I had to change it to 644. What I want to do is automate this process so that any files I create in the same way will automatically be given 644 permissions. I googled this and it seems I need to set umask in /etc/profile I had a look at this file and umask is set to 022, which I believe should set the file permissions to 755. Obviously this isn't happening when I create the file through EditPlus. Can anyone help me out with this?

---

### Post by hellsgate1001 on 2010-03-13
I discovered the problem. I'm using vsftpd and, by default, that sets its own mask to 077 in vsftpd.conf, so all I had to do was edit the umask setting in that file to 022 and restart Ubuntu and all now works as I want it to.

---

