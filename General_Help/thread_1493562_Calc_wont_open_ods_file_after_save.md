---
title: "Calc wont open ods file after save"
date: 2010-05-26
forum: General Help
---

### Post by lynxags on 2010-05-26
Recently I converted my xls files with macros to ods files with macros.  I did this conversion on a windows machine and then migrated the file to ubuntu 10.04.
Now the issue is whenever I open this file and save it, it does not open again until I restart the OS.  Can someone advise?
I get the Calc splash screen and then it goes away without opening calc.

---

### Post by meho_r on 2010-05-26
For starters, try starting Calc from the Terminal (command: **oocalc**), open that file which causes problems and see the output in the Terminal. You may post the output here, so maybe someone can tell you what to do next.

---

### Post by dino99 on 2010-05-26
> **lynxags said:**
> Recently I converted my xls files with macros to ods files with macros.  I did this conversion on a windows machine and then migrated the file to ubuntu 10.04.
Now the issue is whenever I open this file and save it, it does not open again until I restart the OS.  Can someone advise?
I get the Calc splash screen and then it goes away without opening calc.

if i remember well, ooo is able to open xls without changes

---

### Post by lynxags on 2010-05-26
> **meho_r said:**
> For starters, try starting Calc from the Terminal (command: **oocalc**), open that file which causes problems and see the output in the Terminal. You may post the output here, so maybe someone can tell you what to do next.
I do not get any error on the terminal.

---

### Post by lynxags on 2010-05-26
> **dino99 said:**
> if i remember well, ooo is able to open xls without changes
OOCalc does not support xls with macros.  You will have to rewrite macros in Calc so that they work.  And thats exactly what I have done.

---

### Post by lynxags on 2010-05-27
I get an error when I try to save the ods document again.
"Error saving the document. Write Error
The the file could not be written."

---

### Post by meho_r on 2010-05-28
Sounds like permissions problem. Try changing your temporary folder which OpenOffice.org uses. Go to *Tools > Options > OpenOffice.org > Path*, then for **Temporary files** set some folder inside your /home directory, to which you have all required permissions.

If this doesn't help, try checking or unchecking (depending on the state it's in) **Use OpenOffice.org dialogs** in *Tools > Options > OpenOffice.org > General*.

---

### Post by lynxags on 2010-05-28
I tried both options and it does not help.  I would also like to add that I am able to save it once.  It is only when I try to save it second time I get the error.

---

### Post by meho_r on 2010-05-28
Check permissions of your file just to be sure everything's fine there. Can you create a file with some dummy text and macros which behave in the same manner for us to test it? And, of course, you may want to check with OOo forum and/or even file a bug report against OOo.

---

### Post by lynxags on 2010-05-28
I have attached a test file.  I have also opened a defect against OOo.

---

### Post by meho_r on 2010-05-29
I opened the file you provided, enabled macros (must set security to "Medium" for this), entered some text and save it without a problem.

Did you try removing OOo settings (~/.openoffice.org)? Just rename the folder and start OOo, it'll create new default settings.

---

### Post by lynxags on 2010-05-29
> **meho_r said:**
> I opened the file you provided, enabled macros (must set security to "Medium" for this), entered some text and save it without a problem.

Did you try removing OOo settings (~/.openoffice.org)? Just rename the folder and start OOo, it'll create new default settings.
Yes I tried removing .openoffice.org and still it does not help.  I have the Macro settings set to Medium and have to enable macros every time you I open the file. 

According to OOo, the bug may be with Ubuntu release.
[http://www.openoffice.org/issues/show_bug.cgi?id=111890](http://www.openoffice.org/issues/show_bug.cgi?id=111890)
Steps to reproduce:
1. Make a change in the attached document.  Save and close the document.
2. Try to open the document again.  It will not open. You will just see the
splash screen.
3. If the document opens then it will not have the saved changes.

Another thing I noticed is when I try to save the same document twice, I get the
following error.
"Error saving the document. 
Write Error. 
The file could not be written"

---

### Post by meho_r on 2010-05-30
Sorry, bro, but I cannot reproduce the problem. OOo opens and saves this document of yours without problem. Which version of Ubuntu/OOo are you using? I'm using Ubuntu 10.04, 64-bit with OOo 3.2 from repos.

BTW, did you try starting Ubuntu from LiveCD and try from there? What happens? Also, it wouldn't be a bad idea to try with another distro too, from LiveCD maybe, to see if it works there. And, at last, you may try installing vanilla OpenOffice.org.

---

### Post by lynxags on 2010-05-30
Thanks for testing it out.  I am using Ubuntu 10.04. Ooo 3.2 from Ubuntu Software Center on 32 bit machine (PC). 
I do not understand what I am doing wrong then.  I also tried removing and installing OOo but it does not help.

---

### Post by Hagar Delest on 2010-05-30
I remember that one: [Error Saving Document](http://user.services.openoffice.org/en/forum/viewtopic.php?f=9&t=16921). No fix AFAIK.

---

