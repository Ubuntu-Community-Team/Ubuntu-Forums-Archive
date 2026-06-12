---
title: "How to start working with APACHE?"
date: 2012-01-13
forum: General Help
---

### Post by T.exe on 2012-01-13
Hello UbuntuForums..

I am greatly interested in learning APACHE! (This includes learning about implementing by own server, configuring it and the basic operations that can be performed with it!)

I am not intending to do any serious kind of work with servers, just want to spend my college vacations doing some productive learning! :)

Please recommend some good books/videos/sites to start up. I went through certain sites, but I couldn't make up with book to buy, or which site to follow. I usually learn with the help of documentations, but in case of Apache, I'm at LEVEL 0 (No prior experience with servers)!

I greatly  appreciate you help!
Thank you in advance!

---

### Post by Lars Noodén on 2012-01-13
I would recommend starting with the materials over at the Apache web server's site:
[http://httpd.apache.org/docs/2.3/](http://httpd.apache.org/docs/2.3/)

Then from there you will have questions and can look around the net or ask here for specifics.

If you are looking for a place to start, I would recommend setting up two virtual hosts on your machine.  If you can't do name-based virtual hosts, you can do port-based.

If you'd like to start smaller, setting up per-user web directories will also help you get the feel of what a web server is and how it serves pages.

If you want to set up standardized headers, footers and navigation menus then look at Server-Side Includes.  Be sure to set them 'IncludesNOEXEC' for security reasons.  That way you can avoid scripting languages until you actually need them for a full CMS or something else.

---

### Post by T.exe on 2012-01-13
Thank you.. Lars Noodén for your reply! 

I have started with the documentation! :D

---

### Post by coldraven on 2012-01-13
T.exe, I'm like you. My knowledge of servers is almost zero.
I installed Ubuntu server in Virtualbox with the idea that when I broke it it would be easy to just revert back to a fresh install using the Vbox snapshot facility.
You can get ready made server images here:
[http://virtualboxes.org/images/](http://virtualboxes.org/images/)

I have learned how to break it :-)

---

