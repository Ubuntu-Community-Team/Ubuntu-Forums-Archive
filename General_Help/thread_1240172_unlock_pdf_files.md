---
title: "unlock pdf files"
date: 2009-08-14
forum: General Help
---

### Post by jimwes on 2009-08-14
Can not figure how to unlock a downloaded pdf file to read.
Tried xpdf and gimp but all I get is need password.What password??
Login p/w does not work.
Should I down load Adobe pdf reader and some how install it??
Why is the os configured this way??
If I need a p/w why not the login p/w?
Thanks guys- guess you have figured that I am a newbeeee!!
JIM
ubuntu 9.04
dedacated machine just for ubuntu:)

---

### Post by snakeman21 on 2009-08-14
Umm... I don't think that has anything to do with the OS... If the PDF requires a password, it will require a password regardless of what OS you use to open it... Where did it come from?  I get my pay stubs in the form of PDF files, and they always require a password.  Whoever you got the file from must've put a password on it.

---

### Post by Lars Emil Gutt on 2009-08-14
If you downloaded Adobe pdf reader you could make it work with wine from [http://www.winehq.org/](http://www.winehq.org/).
It can make most windows programs work in ubuntu :)

---

### Post by Cheesemill on 2009-08-14
> **Lars Emil Gutt said:**
> If you downloaded Adobe pdf reader you could make it work with wine from [http://www.winehq.org/](http://www.winehq.org/).
It can make most windows programs work in ubuntu :)
 
Why on earth would you want to do this when there is a Linux version of Adobe Reader?
 
Also as snakeman21 said, it will make no difference which reader you use. It is the PDF itself that is password protected.

---

### Post by snakeman21 on 2009-08-14
> **Lars Emil Gutt said:**
> If you downloaded Adobe pdf reader you could make it work with wine from [http://www.winehq.org/](http://www.winehq.org/).
It can make most windows programs work in ubuntu :)

True, but that won't take care of the password...  He'll still need to know the password to open it.

---

### Post by HermanAB on 2010-03-30
When all else fails, edit the file with a text editor and remove the stanza with the password junk.  It should be towards the end of the document.  Since PDF has some error checking, you can just delete a line or two from that stanza, then the reader will ignore it.

---

