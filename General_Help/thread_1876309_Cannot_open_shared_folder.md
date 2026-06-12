---
title: "Cannot open shared folder"
date: 2011-11-06
forum: General Help
---

### Post by Miqueridosims on 2011-11-06
Hello guys:
This is my situation. I am not an IT guy, I am just trying to do make ubuntu run on my own. A few weeks ago I installed Ubuntu server and for now is running, I am able to open shared folder from windows and seems work ok. However, when I try to open the same folder from Ubuntu I am not able. It seems pretty easy but I am a little frustrated. I am able to connect to the server, even I can see the shared folder, which by the way does not have password because when installing the server I had difficulties setting the password, but that is another story.
Can someone of you have a little mercy and shed some light on how can I open the shared folder. By the way I thought would be easier running both on the same system.


Thank you in advance you all.

:confused:

---

### Post by Synoc on 2011-11-06
please give us the read out of 
```
 df -TH 
``` and ```
 cat /etc/fstab 
``` this will tell us what is mounted where, and what format

---

### Post by Miqueridosims on 2011-11-07
Thank you for your respond, and I am going to update this issue.
 In order to understand better the file sharing through Samba I decided to read a little about the samba configuration file smb.conf. I did read the info from Samba website and it was good, I did a practice in another computer how to configure this file and I got it work.
   
  This is what I did to correct this situation (everything was done in terminal)
   
  1.- I created new users in the server and in Samba to start fresh with these users.
   
  2.- I change the SECURITY = SHARE, before I had set the security = user. I still don&#8217;t know what the difference is but did work.
   
  3.- After I got this work I updated my original share and did work as well.
   
  So if you are not expert in Linux / Ubuntu I recommend the following:
   
  -         Learn about linux file system structure.
  -         How to set users through terminal
  -         How to use nano (this is a text editor which helps to modify configuration files).
  -         Learn about Samba configuration file (here is the link )
  -         [http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html](http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html)
   
   
  Hope this helps to anyone who wants to user a file sharing server.
   
  



Regards,

---

