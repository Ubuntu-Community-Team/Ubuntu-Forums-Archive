---
title: "question about /var, /tmp, and /var/tmp"
date: 2010-11-26
forum: General Help
---

### Post by nolag on 2010-11-26
I was reading up on (and posted here inquiring about) moving /tmp to RAM. I was informed that it was a bad idea, since if you do things like burn/rip dvd's /tmp will grow fast. 
 
I was reading further about the issue and read somewhere that bigger files are put in /var/tmp. What is the max file size (by default for ubunut) for files in /tmp? If it is small then I will move it to RAM since larger temp files would be in /var/tmp.
 
Also what is in /var? I know it is things that change when you are using the system, but are any of them needed or can they go to RAM with no loss to the computer?
 
Thanks for any insite :D.

---

### Post by eric3_14159 on 2010-12-24
I don't know about /tmp versus /var/tmp, but I know about /var.

You wouldn't want to put /var into RAM, since it is a place where various groups of files normally get located. If you're running a web server, for example, the files are generally stored in /var/www. This includes all the static HTML, images, and so on.

In the Good Old Days, when we had email delivered directly to our computers, the mail would live in /var/spool/mail/username, I believe, but those times have mostly faded.

/var/games is one of the many locations that games sometimes like to install themselves to.

Good luck in figuring out how to arrange your system. I hope this has been useful.

---

