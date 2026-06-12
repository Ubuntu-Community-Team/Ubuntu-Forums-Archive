---
title: "Beginner's FTP server advice for Jaunty"
date: 2009-12-02
forum: General Help
---

### Post by bedhead75 on 2009-12-02
I'd like to set up a FTP server so that I can have remote access to files in my home folder while I'm away for 10 days.  This would only be for myself and I just want something simple.  I've seen countless references to both vsftpd and ProFTPD.  Which would you recommend?  Or is there something else?  I'd also like it to be encrypted (sftp?) because I guess I'd be logging in with my user name and password right?  Any advice and caveats are appreciated.  Thanks!

---

### Post by DJ Scribblinni on 2009-12-02
I believe your best bet is to use sftp.  SFTP is the encrypted ways of FTP and is the most secure.  It's horridly easy from the get go and requires no configuration out of the box.   This is as easy as installing the openssh-server.  
```
sudo apt-get install openssh-server
```
After that literally you are ready to go.  To test it out simply use whichever client you plan to use and use SFTP and point it to your system.  
You indicated you may be away from your home; you'll need to crack open a port on your firewall facing the outside world, this port in particular is port 22 (unless you've VPN'ed your own network).  
Enjoy.

---

