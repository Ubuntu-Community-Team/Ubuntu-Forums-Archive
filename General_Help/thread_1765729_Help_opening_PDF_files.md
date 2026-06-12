---
title: "Help opening PDF files"
date: 2011-05-23
forum: General Help
---

### Post by tjscool914 on 2011-05-23
Hello, 

I'm trying to view a PDF file from a website.  I've opened this same PDF file numerous times without issue.  Today I tried to open it and received the following message in red:

gedit has not been able to detect the character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again.

I changed my default viewer to epdf and xpdf and received the same error message.  I opened the same pdf file through firefox on my windows pc to see it the file had been corrupted, but it opened fine through windows.  

I dont know what caused the problem with opening pfds all of the sudden, but its really annoying and i cant figure it out.  Please help!

---

### Post by tjscool914 on 2011-05-23
Also, can someone please tell me how to make Document Viewer my default viewer again?  I like the look of it better than epdf.

---

### Post by sanderd17 on 2011-05-23
it's normal that gedit can't open a PDF. I don't know how gedit became the standard. Can you download the pdf and open it with Evince documentviewer? Press ALT+F2 and type

```

evince

```

If this works, than you can change the default settings: right click on any pdf and go to properties, there you can select the default application. If it still doesn't open right in firefox without first downloading, you can go to your firefox preferences, and under the applications tab, select the application "documentviewer" for pdf files.

---

### Post by tjscool914 on 2011-05-23
Hey... i tried what you said.  I right clicked a pdf file i had saved on a flash drive and set Document Viewer as the default viewer.  I then went back on the web to open the pdf file that was giving me problems.  When i clicked on it, the window still displayed epdf as the viewer to open it with, but this time it worked.  I dont quite understand why but its working now.

---

### Post by sanderd17 on 2011-05-23
and did you check the firefox settings?

---

### Post by tjscool914 on 2011-05-23
Do you mean the settings under the applications tab in preferences?  I looked in there for something to change, but I didnt see anything relevant to a document viewer.

---

### Post by sanderd17 on 2011-05-23
yes, you should search for "PDF" and if documentviewer is not included as one of the possibilities, add it yourself. It's the file /usr/bin/evince

---

