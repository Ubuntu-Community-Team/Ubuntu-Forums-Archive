---
title: "Help to install and run Windows programs on Ubuntu"
date: 2010-05-06
forum: General Help
---

### Post by Mav0863517 on 2010-05-06
Hi everyone
I have couple of programs on Windows 7 I really like to use on Ubuntu
(MSN messenger , FlashGet , Manga Studio EX , Internet Download Manager)
i check the main site for each of the programs and found out they don't have Linux version.
is there a method to be able to install and run these programs on Ubuntu?

---

### Post by sgosnell on 2010-05-06
Install wine, install them using it, and they should run.  Not all Windows programs will run under wine, but most do.  Empathy and Pidgin are excellent IM clients that can use the MSN protocol.  I don't know about the rest, but I think you'll find that Linux has better download managers than IE.

---

### Post by alexpwnsn00b2 on 2010-05-06
like previously state wine is a great too to run most windows programs

---

### Post by eakergd on 2010-05-06
Playonlinux seems to be a pretty good front end for Wine.  You can download it from the Ubuntu Software Center.

---

### Post by Mav0863517 on 2010-05-06
thanks for the reply guys I will try wine now 
Can you recommend me some download managers?

---

### Post by nbulchandani on 2010-05-06
Well,about internet messesngers: pidgin,psi,kopete,empathy are great...and ofcourse there would be many more choices..idm is a thing i would say linux lacks..but there are a plenty of good download managers to satisfy you.And yeah if you have heard Gigaget ;a good download manager works pretty well under Wine.Give it a try.To cite one;i have personally tried GWget it works good.
regards

---

### Post by Mav0863517 on 2010-05-06
I installed Wine successfully
however I tried to install couple windows programs and I always get this error [http://img442.imageshack.us/i/94726875.png/](http://img442.imageshack.us/i/94726875.png/)[IMG]http://img442.imageshack.us/i/94726875.png/[/IMG]

---

### Post by Bradj47 on 2010-05-06
> **sgosnell said:**
> Empathy and Pidgin are excellent IM clients that can use the MSN protocol.  I don't know about the rest, but I think you'll find that Linux has better download managers than IE.

This may now be off-topic but I agree that Pidgin is a really good IM client that supports the MSN protocol and more.

---

### Post by 3rdalbum on 2010-05-06
Go into a terminal, type 'wine' without the quotes, and then drag the file onto the terminal.

Wine is a great project, but statistically it only runs 20% of Windows software. Find Linux equivilants wherever possible and use Wine as a last resort.

---

### Post by sgosnell on 2010-05-06
You need to do what it says, and read up on the executable bit, by clicking on the link.  In short, you need to make the .exe file executable.  You can do that by opening Nautilus, the file manager, by clicking on Places, navigate to the file, right-click on it, select Properties, then on the Permissions tab check the box that says "allow executing file as program".  That tells the system that the file is a program, not some other type of file.  Then you should be able to double-click it and have it run in wine.  If that doesn't work, right-click on the file and open it with wine.

---

### Post by Mav0863517 on 2010-05-07
Thank you all for all the great reply
 I'm using Gigaget for download and Empathy as Messenger.
 I can also Install and run Windows programs now,but sadly not all of them work.
 Is Wine the only method to install and run Windows programs now?

---

### Post by sgosnell on 2010-05-08
Yes, wine is it, AFAIK.  You can't run Mac programs, either, nor can you run Mac or Linux programs in Windows, etc.  They're completely different operating systems, and nothing is completely compatible.  If you really want to run all Windows programs, you should just run Windows and forget about Linux.

---

### Post by Mav0863517 on 2010-05-08
ah ok
I just started to use Ubuntu lately and I'm enjoying it.
I'm considering to have Ubuntu as my main operating system because it has great features
but I keep going back to Windows 7 because some programs I have there don't have Linux version yet.

---

