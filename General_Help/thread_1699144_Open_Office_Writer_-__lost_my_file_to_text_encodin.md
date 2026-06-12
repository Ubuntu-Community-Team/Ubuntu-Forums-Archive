---
title: "Open Office Writer -  lost my file to text encoding"
date: 2011-03-03
forum: General Help
---

### Post by iochinome on 2011-03-03
Hello everyone,

I was working on a text file in open office writer last night, and this morning i tried to open it and a little thing popped up saying "ASCII Filter Options," prompting me for which character set, language and default fonts I wanted to use. (only after it asked if i wanted to recover the document, which i just did since it was asking me...)
Now the document, which was very important, is a scrambled bunch of random characters! I cannot find the correct character set. Why is it prompting me for which character encoding I am using in the first place? 
I would really appreciate some suggestions for how to take care of this and retrieve my files. Thanks!

- Iochi

---

### Post by LinuxH4x0r on 2011-03-03
set it to "Encode in ANSI"

---

### Post by grahammechanical on 2011-03-03
First, when Open Office asks me if I want to recover a document it is because I have previously closed Open Office without saving the document. May be I shut down the OS with Open Office still open. Or something like that.

Second, may I ask if this document you were working on was a document created in Open Office? Perhaps it was a document created by a program running on another OS? In this case the character encoding might have been worked out by Open Office without you knowing anything about it. If you had saved the program then you might have been given a choice as to the file format to save in. Use the Open Office format and the character encoding would have been chosen automatically.

Third, are you reading this post in firefox? If so, go to the View menu and select Character Encoding. You will see a list of possible character codes. Western (Windows-1252) might be the code for the document you were working on. Provided that I am guessing correctly.

Regards.

---

### Post by iochinome on 2011-03-03
Thanks guys!
LinuxH4x0r, where do i set it to "encode in ANSI"?? It is not immediately obvious, nor does it list it in the index or help section.

grahammechanical, yes, I did create this in openoffice, last night actually, and I went back and tried all of the different encodings listed in firefox and none of them worked. 
any more suggestions? I would really appreciate the help. Thanks!!

- Iochi

---

### Post by grahammechanical on 2011-03-03
So, my big idea was wrong. Sorry. I thought may be it was a Rich Text Format file produced by Microsoft Windows.

I have tried going through all the Open Office menus to find something on character encoding. And there is nothing.

Does the file open in Open Office? What font is listed? How about selecting the text and changing the font? Perhaps the file was saved as a web page - html. Under the View menu is Print layout ticked or Web Layout? Could you try saving the file as in Open Document format? Did you save it as a PDF file? Could you try opening it in Text Editor or Evince?

When the sensible things don't work, try the stupid things. That is the way my mind works.

I was just about to post this message, when I decided to test my own theories. I have loaded Open Office and I am about to open a PDF file and I have been give a dialog box called ASCII Filter Options. It shows the character set (unicode UTF -8. the default font (freeserif in my case) and the language (English UK in my case). Now I am about to click OK

I guess I see those random characters that you describe. Do you see at the top of the page %PDF-1.4? If so then you are looking at a PDF document that has been opened in a word processor. Try opening it in Evince.

Hope some of this works.

Regards.

---

### Post by AlphaLexman on 2011-03-03
@ the OP:
The format 'Open Document Text' is really just a compressed zip file with xml and other formats...

Can you open the original file with the 'archive manager'? You will see **all** the source files.

---

### Post by ameximes on 2011-03-03
Just a suggestion: Take a backup before doing any thing more.

Send your file (or a part of your file which you ensure that not including any sensitive information) or a screenshot of the file to give us a clue. Sometimes the characteristic of "a bunch of character" is directly tells the solution to experienced eyes.

And yes, open a copy of your file with archive manager and check the files with gedit.

---

