---
title: "scanner problem"
date: 2011-01-23
forum: General Help
---

### Post by wombil on 2011-01-23
Hey Guys,
I have ubuntu 10.04.1 and a H.P.psc 1311 all-in-one printer scanner.Printer works ok but when trying to scan,with xsane,it goes through the scanning process and an image of the document comes up on the screen.
 When I try to save this image to desktop or file/folder whatever I get the message;
           "Child Process Error.
Failed to execute OCR command:GOCR:no such file or directory."
 Is there a fix for this and what is wrong?
 I have been thinking of upgrading to 10.04 or10.10,
Maybe that will end the problem but I like 8.04
 All help appreciated,thanks.

---

### Post by wombil on 2011-01-23
The fix was to install gocr [didn't know it had to be done.]
 Open console and enter, gocr -h 
That installs gocr and all is well.

---

### Post by ronnielsen1 on 2011-01-23
You might also look at simple-scan and gscan2pdf. I love gscan2pdf

---

### Post by wombil on 2011-01-23
Yes,thanks mate,
 I was just thinking ,"Why doesn't the error message just say to install gocr instead of all that gobbledgook." Maybe it isn't mystical enough.
 I believe in the kiss system.

---

