---
title: "Super slow Internet Explorer 9.04"
date: 2009-07-23
forum: General Help
---

### Post by superconfusednoob on 2009-07-23
I just downloaded wine and cabextract.  I then downloaded and installed ies4linux.  I extracted the file, and clicked OK on the box that came up.  It came up with an error message. But as I xed out of it, there was a new icon on my desktop.  I double-clicked it and it brought me to internet explorer.  It worked.  Horray!  But, it also ran extreeeemely slow. Firefox works like a charm.  Any idea as to why this is happening?  What should I do to get it running at optimal speeds?  I installed ubuntu 9.04 this week.  I have had it for 3 days.  It is completely forign to me.  Easy steps would be greatly appreciated!!  Thanks in advance!

---

### Post by c0mput3r_n3rD on 2009-07-23
Did you follow [these]("http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu") instructions?

---

### Post by philcamlin on 2009-07-23
: 1) Open a terminal 
2) Open /etc/apt/sources.list 
  sudo gedit /etc/apt/sources.list
3) Uncomment (or add) following lines: 
  deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy universe
4) Add this line: 
  deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
5) Close gedit. Update and install wine and cabextract: 
  wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
 sudo apt-get update
 sudo apt-get install wine cabextract
6) Download IEs 4 Linux and install 
  wget [http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz](http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz)
 tar zxvf ies4linux-latest.tar.gz
 cd ies4linux-*
 ./ies4linux

edit: ohh looks like the guy above beat me to it :P

---

### Post by superconfusednoob on 2009-07-23
> **c0mput3r_n3rD said:**
> Did you follow [these]("http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu") instructions?


I tried to follow them.  I think I did it correctly. Both numbers 3 and 4 were copied and pasted in to the new window that popped up after entering in number 2.  After I did all this, it appeared to be working, then, as before, and a message popped up in my terminal. It said something like "it is developed to use with recent wine versions. It is recommended that you update wine."  I thought I did this in step 5?  I'm confused...

---

### Post by superconfusednoob on 2009-07-27
It asks for my password, but i cannot type anything, or copy and paste my password.  Any reason why?

---

