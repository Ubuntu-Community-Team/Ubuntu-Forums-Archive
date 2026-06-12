---
title: "Trying to crack a password on a pdf ..."
date: 2010-08-12
forum: General Help
---

### Post by josephellengar on 2010-08-12
Hi all!  I'm trying to crack a password on a pdf document.  I have been using pdfcrack from the repositories but when I run the command pdfcrack -f filename I get the error:  
Encryption not detected (is the document password protected?)

I get the same error if I add the -o or -u option.  Does anybody know how to do this?  Strangely, I can get into the file just by opening it in foxit in Windows, but when I save it elsewhere it is still password protected, so I need the real password.  (Can't print to pdf in foxit in Windows)

---

### Post by dino99 on 2010-08-12
as you can open it with foxit, you may have an "empty" password

---

### Post by josephellengar on 2010-08-12
> **dino99 said:**
> as you can open it with foxit, you may have an "empty" password

Nope, not an empty password.  I can't even enter an empty password.  The enter button is grey.  And it's not just space either.  Strange.

---

### Post by dcollier on 2010-08-12
Try adding the pdf as an attachment in an email. And open it from the email. It worked for me with a password protected word document.

---

### Post by josephellengar on 2010-08-12
> **dcollier said:**
> Try adding the pdf as an attachment in an email. And open it from the email. It worked for me with a password protected word document.

Bizarre.  Solved.  That pdf worked, but I tested it out with another pdf with a longer password and it didn't work.  Thank you so much!

---

### Post by dcollier on 2010-08-12
Glad to hear that it worked!

---

