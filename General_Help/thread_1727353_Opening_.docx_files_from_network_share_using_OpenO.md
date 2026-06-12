---
title: "Opening .docx files from network share using OpenOffice 3.2"
date: 2011-04-12
forum: General Help
---

### Post by metallica1973 on 2011-04-12
I have to use and update many documents on a network share in my organization. I am using OpenOffice 3.2 (latest and Greatest). When I go to the document that I need via the network share, I can open up the document no problem at all but the minute I attempt to save it, it will freeze and I have to:

[php]pgrep soffice| xargs -i kill -9 {}[/php]

to kill it. To get it to work I have to save the document from a .docx format to a .doc format then all works well. Unfortunately, all of my coworkers use the lastest and greatest of MS Office. 

??

---

### Post by Mark Phelps on 2011-04-12
Do these documents have sharing turned on by default?  If so, it could be that OO is trying to synchronize the sharing features and getting hung up in the process.

You might have to turn off Sharing before you save the document.

I run into this same problem with Excel documents all the time and AM using actual MS Office 2007 on them.

---

### Post by metallica1973 on 2011-04-12
When you say sharing is this to be turned off on the properties of the file on the network share or through open office?

---

### Post by SeijiSensei on 2011-04-12
Why don't you make a local copy of the document(s) on your desktop first and edit those?  It's going to be a lot faster than working over the network anyway.  When you're done, just copy them back over to the server.

---

### Post by Mark Phelps on 2011-04-12
> **metallica1973 said:**
> When you say sharing is this to be turned off on the properties of the file on the network share or through open office?

So, it could be that the original Office document has sharing turned on, and Open Office either won't allow you to disable that, or does not understand how to turn it off.

Sorry ... personally found Open Office not useful for working actual Office 2007 xml documents.  Only know how to turn sharing off in actual MS Office 2007.

---

### Post by metallica1973 on 2011-04-12
Actually Gents I just downloaded ABIWORD suggested from another forum and all works well at least until Oracle fixes this issue.

[http://askubuntu.com/questions/32691/what-do-you-use-to-edit-microsoft-word-documents-docx](http://askubuntu.com/questions/32691/what-do-you-use-to-edit-microsoft-word-documents-docx)

---

### Post by rewyllys on 2011-04-12
IMHO the easiest way of handling the problem of  .docx files is to install LibreOffice.  Here is a thread that explains how to do so:

[http://ubuntuforums.org/showthread.php?t=1720769](http://ubuntuforums.org/showthread.php?t=1720769)

---

### Post by frogotronic on 2011-04-12
> **metallica1973 said:**
> Actually Gents I just downloaded ABIWORD suggested from another forum and all works well at least until Oracle fixes this issue.

[http://askubuntu.com/questions/32691/what-do-you-use-to-edit-microsoft-word-documents-docx](http://askubuntu.com/questions/32691/what-do-you-use-to-edit-microsoft-word-documents-docx)

Install LibreOffice - it works really well with M$ Office 2007

[https://launchpad.net/~libreoffice/+archive/ppa](https://launchpad.net/~libreoffice/+archive/ppa)

- CH   :popcorn:

---

