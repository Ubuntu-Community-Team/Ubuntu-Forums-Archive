---
title: "Need help setting up an FTP server"
date: 2011-08-03
forum: General Help
---

### Post by Jesse B on 2011-08-03
Me and a bunch of friends have all embarked on a rather large project,  and I'm trying to ease the sharing of files.  Since I have a server  sitting around and not getting much use, I figured I could make an FTP  server where people can just drop/grab the files we need. 

I have never done anything like this, and have never even exposed  anything externally, so I'm a bit hesitant.  I also just don't know  which protocols or packages to use, and have even less of an idea how to  configure them. 

Basically here is what I want to achieve: 
- SECURE access to my sever 
- Separate user accounts for each person (mostly for logging purposes) 
- Each user is confined to a single, specified directory, and can upload/download files from here 

I've seen people recommend using FTPS via the vsftpd package, and  use SSL.  I've also see people just suggest installing the  OpenSSH-server package and using SFTP. 

No real idea what I'm doing here, so suggestions would be fantastic! :D  

Thanks guys, 


- Jesse

---

### Post by zero2xiii on 2011-08-06
This is a rather large project, but I can help you.

Where do you want me to begin? Have you done anything yet?

---

### Post by tredegar on 2011-08-06
Perhaps you should look at [sshfs]("http://fuse.sourceforge.net/sshfs.html")
It is in the ubuntu repositories.

---

### Post by galvatron408 on 2011-08-06
maybe you should use [www.dropbox.com]("http://www.dropbox.com")

it's free

btw, i just tried it now and it is AWESOME!

---

### Post by Jesse B on 2011-08-06
Thanks for your input everybody.

After discussing things with a friend of my, I actually opted to use Subversion rather than just FTP.  This will help us with version control, which will be very useful with 8 people all working on different files.  Still in the process of getting things configured however.

EDIT:  I did consider Dropbox, as I use it for personal use, but I'm just not sure 2GB of space will be enough for us.  We're going to be working with some fairly large files.

---

