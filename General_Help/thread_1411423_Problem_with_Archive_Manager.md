---
title: "Problem with Archive Manager"
date: 2010-02-19
forum: General Help
---

### Post by Salestar on 2010-02-19
Hello all, this is my first post, so be gentle. I've been searching all over this and other forums to try to find the answer, and basically the only answer I get is... Well, you'll see.

So, here's the situation. I'm trying to install World of Warcraft on my Ubuntu machine through WINE. I just built this computer from scratch last month, it's a pretty nice machine, and I haven't had any problems with it up to now. I've gotten WoW installed, patched, and working up to the log-in screen. When I try to log in, it gives me this error:

"Microsoft Visual C++ Runtime Library

Runtime Error!

Program: C:\World of Warcraft\WoW.exe

R6034
An application has made an attempt to load the C runtime library incorrectly. Please contact the application's support team for more information."

Like I said, I've searched all kinds of forums, and the linux solution I come up with is to install a C++ redistributable package thingy as can be found here: [http://www.microsoft.com/downloads/en/confirmation.aspx?familyId=200b2fd9-ae1a-4a14-984d-389c36f85647&displayLang=en](http://www.microsoft.com/downloads/en/confirmation.aspx?familyId=200b2fd9-ae1a-4a14-984d-389c36f85647&displayLang=en)

Whenever I try to install that, seeing as it's from Microsoft and an .exe file, I get this message from Archive Manager:

Archive:  /home/thaddius/Downloads/vcredist_x86.exe
[/home/thaddius/Downloads/vcredist_x86.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/thaddius/Downloads/vcredist_x86.exe or
          /home/thaddius/Downloads/vcredist_x86.exe.zip, and cannot find /home/thaddius/Downloads/vcredist_x86.exe.ZIP, period.

I need your guys' help to figure out how to get this working. I've tried the program through WINE, but I am clueless as to how to do this, and I'm 50% sure I didn't do it right. I'm pretty new to Ubuntu, so any solutions or anything would be helpful. If I posted this in the wrong forum, forgive me, like I said, it's my first time and I figured "general help" sounded good enough for me.

Thank you so much,
-Leon

---

### Post by cchhrriiss121212 on 2010-02-20
An .exe is a Microsoft executable file so you need to right click and install using wine. It should be fairly straightforward.

---

### Post by Salestar on 2010-02-20
Wow, that was... extremely straightforward. Thank you so much!

---

