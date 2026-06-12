---
title: "Campus internet"
date: 2012-03-25
forum: General Help
---

### Post by batophobia on 2012-03-25
So my college campus has a wifi network (yay!)  Problem is there is some excessive security.  Line one is the wifi password, which is no problem since they sent it out and everything is all good there.  My problem comes from the second part.

Have you ever been to a hotel or restaurant or somewhere that has wifi but to access the internet you have to go through a special web page?  Well my college has something like that, where it will block most internet activity until you reach that website and enter a username and password (which I have an account so I can get in).  However, when running Ubuntu 11.10 in terminal (ctrl + alt + F1) I often run into issues where I have been locked out as the certificate from the campus web-blocker is only good for 24 hours.

So, is there some way I can log in from the terminal?

---

### Post by Earsplit on 2012-03-25
Try installing Lynx, a CLI web browser.  Set it to allow cookies and simply bookmark the login site.  Why do you have to use the tty terminals? Couldn't you just pop into your browser and reenter the password daily?

---

### Post by batophobia on 2012-03-25
Well that's what I've been doing but I'm attempting to run a server on that machine since it is a laptop I rarely use for anything.  I will look into lynx, thanks for the reply.

---

### Post by Earsplit on 2012-03-25
You could probably ask the IT at your school to bypass daily authentication. I have a server set up at my school and had to go through pretty much the same thing.  I ended up getting a static IP for my box and a matching certificate.  They reset the internet weekly, and the same thing would happen.

Good luck!

---

### Post by batophobia on 2012-03-26
Sadly I know some of the people on IT and have talked to them about it but apparently the college is fairly strict and they will not allow anything like that.  I even had troubles with my consoles connecting and they wouldn't give me permissions to connect through those.

---

