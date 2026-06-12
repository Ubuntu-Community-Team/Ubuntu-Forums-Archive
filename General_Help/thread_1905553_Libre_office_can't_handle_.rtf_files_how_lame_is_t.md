---
title: "Libre office can't handle .rtf files? how lame is that?"
date: 2012-01-07
forum: General Help
---

### Post by internetprofiles1 on 2012-01-07
Well its been about 3 months of exclusive UBUNTU OS 11.10 and I've had not even had to go to my virtualbox  dual boot for incompatible websites thanks to the firefox 8 upgrade. things seem to be going fine however I must comment that libre office is terrible and is no way close to openoffice. I have tried to revert back to openoffice but I seem to have trouble getting that to work because there are so many steps involved to get it working. I'd hate to have to dual boot windows just because I need a reliable officesuite/ word processor. Has anyone managed to revert to openoffice using the deb packages they provide, or is there a fix for libre to open and properly view the most basic of documents an rtf file? or another program for office:confused:

---

### Post by ubiquitin.jf on 2012-01-07
What exactly is the problem you're having with RTF files? LO opens, edits and saves them perfectly on my machines.

---

### Post by coffeecat on 2012-01-07
Libre Office handles RTF files just fine for me too. Which app were your RTF files created in? Have you tried a variety of RTF files to test LO with?

---

### Post by internetprofiles1 on 2012-01-07
well thats strange. Its an online class file. When the rtf document open in Libre writer its shows a few words and the rest of it is blank pages. To make sure it was not a corupt file, I went to my XP virtualbox and downloaded and opened the same file with openoffice and it opened fine. Could it be a ubuntu issue?

---

### Post by wyliecoyoteuk on 2012-01-07
Unlike enriched text, rich text or .rtf files are actually a Microsoft file format, which it is deprecating from office 2010 onwards. 
So not the "most basic" format.

Different versions of MS office will produce slightly different types of  .rtf file (there are about 8 versions).
It is possible that LO does not recognise a particular control word that OOo does.

---

### Post by claracc on 2012-01-07
You can install the deb openoffice package in the official openoffice.org site following the method described in this link: [http://user.services.openoffice.org/en/forum/viewtopic.php?t=68](http://user.services.openoffice.org/en/forum/viewtopic.php?t=68)

---

### Post by internetprofiles1 on 2012-01-07
a google search did show other people having this problem but no fix so i thought it was a libre issue. 
ok tried some more stuff, uploaded the same file to my ubuntu one account opened it on a windows PC and it works fine. so its not a ubuntu download glitch. With Libre it seems to be only showing the headers and not the text body, nor keeping the table format... The best I suppose is to attach it to the forum and seem if anyone with libre can open it...oops its too large to upload
Another thing i tried was I opened the file in libre I clicked on "file" then "preview in web browser" and I was able to see all the text it just was not formatted properly... how do I remove libre  and just reinstall it? i wondering if that is a fix.

---

### Post by internetprofiles1 on 2012-01-07
> **claracc said:**
> You can install the deb openoffice package in the official openoffice.org site following the method described in this link: [http://user.services.openoffice.org/en/forum/viewtopic.php?t=68](http://user.services.openoffice.org/en/forum/viewtopic.php?t=68)


thanks those steps seems a lot simplier I will try it.

---

### Post by mastablasta on 2012-01-07
i had a problem with latest LO opening files, so i used a bit older stable version and it worked better.

---

### Post by internetprofiles1 on 2012-01-07
> **internetprofiles1 said:**
> thanks those steps seems a lot simplier I will try it.



Yesssss openoffice works and so does my file. I really don't know what was wrong with libre, I figured how to use Synaptic Manager to completely remove all the libre packages and removed all the remnants of the openoffice package i had previously tried to install  and then I followed those steps to get openoffice install, it worked like a charm.Surprising that that openoffice tutorial was posted in 2007 , and it still works today. Maybe i had a conflict and reinstalling Libre would have also worked

---

### Post by gshreya3 on 2012-04-23
Hello All,

I am also facing the same problem with rtf format. RTF file opens in libre office but scattered data.
I dont want to change the format of the file.
Please help me on this line.

I tried the rtf format using Open-Office but problem remained same. These formats were clearly seen in Microsoft Office.
Then what may be the problem in open office and libre office

Thanks in advance.

---

### Post by gshreya3 on 2012-05-04
Please visit - 
[http://en.wikipedia.org/wiki/Rich_Text_Format](http://en.wikipedia.org/wiki/Rich_Text_Format)

Let me know if there is any other solution for editing files other than rtf format.
Please do th needful

Thanks in advance.

---

### Post by ipadm on 2012-06-06
Faced the same problem and created bug report [https://www.libreoffice.org/bugzilla/show_bug.cgi?id=50775](https://www.libreoffice.org/bugzilla/show_bug.cgi?id=50775) 

So please confirm it there, for developer to see the confirmed bug.

---

### Post by timgood on 2012-06-06
I have also had a number of problems with LibreOffice which do not seem to exist in OpenOffice, including handling of animated gifs in Impress, random loss of images (retaining only placeholder) and random crashes (though autorecovery has meant I have not lost a lot of work). 

These problems make it difficult for me to recommend Ubuntu as a 'slot in' replacement for Windows machines and I am hoping that they will be fixed soon (though the gif issue has now been a known bug since LO version 3.4 and not been fixed). If not, can we have a less buggy Office suite as the default in 12.10 please?

---

### Post by ipadm on 2012-06-06
> **timgood said:**
> I have also had a number of problems with LibreOffice which do not seem to exist in OpenOffice, including handling of animated gifs in Impress, random loss of images (retaining only placeholder) and random crashes (though autorecovery has meant I have not lost a lot of work). 

These problems make it difficult for me to recommend Ubuntu as a 'slot in' replacement for Windows machines and I am hoping that they will be fixed soon (though the gif issue has now been a known bug since LO version 3.4 and not been fixed). If not, can we have a less buggy Office suite as the default in 12.10 please?


Did you created BugReports? If you will do it then we will have less buggy Office suite as the default in Ubuntu! It's simple to do and developers making bugfixes fast.

---

### Post by timgood on 2012-06-07
Yep. Most are known bugs, but I have submitted my own as well. Still nothing fixed. As far as fast bug repairs go: animated gif problem reported 8th November 2011 and still reported not fixed with most recent version, and developments. [https://bugs.freedesktop.org/show_bug.cgi?id=42709](https://bugs.freedesktop.org/show_bug.cgi?id=42709)

---

