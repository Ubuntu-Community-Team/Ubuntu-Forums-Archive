---
title: "Looking for some help with a file upload/PHP"
date: 2009-08-05
forum: General Help
---

### Post by Jago6060 on 2009-08-05
The Ubuntu Forums have so many intelligent people, I figured I'd post this issue here as well and see if anyone had a solution.

I administer a website, and up until recently, there was a feature for my client to upload pdf's(their newsletter).  The code is unchanged and has been running fine for about 2 years now.  The problem now is the file will upload, but when you open it through the browser, it says "File is damaged and cannot be repaired".

I've tried alternate routes to try to isolate the problem.  Direct ftp upload, upload with built-in PHP script, upload with service provider's upload feature.  Nothing seems to correct this problem.  The file is fine and viewable up until it gets uploaded to the hosting service.  Any ideas?

---

### Post by credobyte on 2009-08-05
Upload it to your server, download from your server, open it .. still viewable ? Have you tried to upload it in ASCII mode ( FTP ) ?

---

### Post by Jago6060 on 2009-08-05
Upload then download still causes the file to show an error.  BUT I tried ftping the pdf in ASCII mode, then grabbing it with ftp to my Desktop, and it worked!  So the problem is file encoding.  So I guess my next step is to figure out how to convert a pdf to ASCII with PHP.  Anyone know how?

---

