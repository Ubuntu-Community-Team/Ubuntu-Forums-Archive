---
title: "How do I apply breaks in text files?"
date: 2011-03-31
forum: General Help
---

### Post by darkcoffee on 2011-03-31
I do not know what happened.  But when I move the text files back and forth between Windows and Linux, the enters/paragraphs gets messed up and square characters appears.  And I think it got worse when I deleted those squares.  So now it is one very long line.  

How do I get the long line to break every 50 characters but not having the last word get cut off mid-word?  

I am thinking "cat textfile > something" but I do not know what that something is.

---

### Post by Karlchen on 2011-03-31
Hello, darkcoffee.

I assume that what you see is caused by the fact that by default

[LIST]
[*]Windows editors, namely Notepad, will save linebreaks as CR-LF (carriage return / linefeed)
[*]Linux editors will save linebreaks as LF (linefeed) only
[/LIST]

One approach to avoid any problems caused by the differing linebreak encoding is:
On Windows use a text editor which can read and write Linux textfiles, too, i.e. it can read and write linebreaks as linefeed.
The text files should be transferred between the Windows machines and the Linux machines in binary mode only. (This is most relevant if the files are transferred via FTP.) If they are copied via Samba shares they will be copied in binary mode anyway.

About setting line length to 50 characters:
A more common default value would be 78 or 80 characters. But anyway, any not too stupid text editor will allow you to define a maximum line length and insert the appropriate linebreak sequence whenever appropriate. You will have to consult the helpfile coming with the editor that you use in order to find out where the line length can be defined.

HTH,
Karl

---

