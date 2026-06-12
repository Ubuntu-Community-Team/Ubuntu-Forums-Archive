---
title: "Issue with Libre Office"
date: 2011-02-06
forum: General Help
---

### Post by mannyweb.ca on 2011-02-06
Well I just installed Libre Office, unfortunately I get an annoying error everytime I start it.
   
I get a pop up that says the following:

[B]Error loading BASIC of document
file:///home/something/.libreoffice/3/user/basic/dialog.xlc/:
General Error.
General input/output error.[/B]

Thus far LibreOffice works well, this ever seems to more than an annoyance if anything, but either way.  

How do I fix this?

---

### Post by mannyweb.ca on 2011-02-08
Anybody?

:popcorn:

---

### Post by fragos on 2011-02-09
I checked my install of LibreOffice and that file on my system is an empty Calc spreadsheet file as is script.xlc in that same folder. I get no messages like yours and am unsure of the purpose. I'd try creating a new dialog.xlc file to replace yours. Start Calc and save the empty spreadsheet to make a new one. Just a guess but don't see how you can do any damage by doing what I suggest.

---

### Post by mannyweb.ca on 2011-02-11
^Well you're definitely on to something just noticed that this 

[B]file:///home/something/.libreoffice/3/user/basic/dialog.xlc/

[/B]doesn't even exist so running a search I found two paths

**opt/libreoffice/basis3.3/share/basic/dialog.xlc**

and

[B]opt/libreoffice/basis3.3/presets/basic/dialog.xlc

[/B]So I'm assuming that somehow I have to change the path to whichever one is the correct. 

So anybody know what I'm talking about and if so how to accomplish this???

---

### Post by fragos on 2011-02-11
The .libreoffice folder should have been created when you first ran the LibreOffice as a user. The /opt path is where the the initial values came from.

---

### Post by mannyweb.ca on 2011-02-11
^ Hey thanks a lot I got this fixed.  So I noticed that .libreoffice is a hidden folder and I did what you initially recommended which was create a new dialog.xlc.  

Don't have that annoying pop up anymore.  Again thanks a lot.

---

### Post by hypertrike on 2011-02-18
I had the same problem.
Specifically, to solve it, I used Nautilus (standard 10.04 file manager), went to .libreoffice/3/user/basic, right clicked on the "script.xlc" file that I found there and chose gedit to open it, deleted everything in that file then did a "save as" to save an empty file called "dialog.xlc"

The next time I ran LibreOffice, no more error messages. :D

---

### Post by frogotronic on 2011-03-14
> **hypertrike said:**
> I had the same problem.
Specifically, to solve it, I used Nautilus (standard 10.04 file manager), went to .libreoffice/3/user/basic, right clicked on the "script.xlc" file that I found there and chose gedit to open it, deleted everything in that file then did a "save as" to save an empty file called "dialog.xlc"

The next time I ran LibreOffice, no more error messages. :D

Excellent, this worked for me as well.  Can you mark this thread as "SOLVED" ?

- CH

---

### Post by ecatodarcus on 2011-06-09
That worked for me also!!thanks!!

---

### Post by Rolandmaffia on 2011-10-22
Thanks, solved - I've just created the plain documents what it missed, then it doesn't prompting the error anymore.

---

### Post by acceptancegroup on 2012-02-03
Same issue with running LibreOffice 3.4.4. 

Could NOT find:
file:///home/something/.libreoffice/3/user/basic/dialog.xlc/

Instead I found:
file:///home/something/.libreoffice/3/user/basic/script.xlc/

I left this file and added a copy of: /script.xlc that I renamed to: /dialog.xlc.

I now have BOTH files in the directory:
file:///home/something/.libreoffice/3/user/basic/
script.xlc
dialog.xlc

It worked fine.

I could NOT find the path in this version:
opt/libreoffice/basis3.3/share/basic/dialog.xlc
or
opt/libreoffice/basis3.3/presets/basic/dialog.xlc

So only one change was made to the above described path:
file:///home/something/.libreoffice/3/user/basic/

---

