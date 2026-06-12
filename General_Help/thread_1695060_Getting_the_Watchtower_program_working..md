---
title: "Getting the Watchtower program working."
date: 2011-02-25
forum: General Help
---

### Post by Bcrowes11 on 2011-02-25
Hi I'm running Ubuntu 10.10, and I installed the Watchtower Library 2010 and it won't work. I click on the icon and the mouse starts showing that it's loading, but that's all it does. I tried the exe file in the program folder. I tried in the wine folder, I checked for the iphlpapi.dll fake file and the so file. Still isn't working. I made sure I've got 1.3.14 version of wine. What else is there to try? I really need to get this working please. Thanks.:confused:

---

### Post by edhplus2 on 2011-02-25
Mine works in 10.04 and also worked in 10.10.
Sounds drastic, but have you tried starting over? The less drastic way is to delete the (hidden) .wine directory in your home folder. Then re-install the Wt Library. The way I installed it is by using nautilus to go to the CD and right-clicking on setup.exe, then choosing open with Wine Windows Program Loader.
More drastic is to remove wine, then delete the folder, then install wine.
Deleting that .wine folder removes any Windows programs you have installed, since that is where wine puts them.
On the positive side, backing up that folder and restoring it if you have to reinstall the operating system will sometimes save you the time of re-installing the program.
You shouldn't need that customized .dll file with the 1.3... version of wine.
There is a or support page at [http://appdb.winehq.org/](http://appdb.winehq.org/), more specifically at [http://appdb.winehq.org/objectManager.php?bShowAll=true&bIsQueue=false&bIsRejected=false&sClass=version&sTitle=&sReturnTo=&iId=22127](http://appdb.winehq.org/objectManager.php?bShowAll=true&bIsQueue=false&bIsRejected=false&sClass=version&sTitle=&sReturnTo=&iId=22127)
But it sounds like you have been there if you know about the required version and .dll.
I don't know how to troubleshoot it any more than what I have said, but let us know if you try the suggestions and it works or doesn't.
I do remember having a problem with it the first time, but starting clean with wine and the Library must have worked.
-Ed H

---

### Post by Bcrowes11 on 2011-02-25
THANK YOU SO MUCH!!! THIS WORKED!!!:P:D:popcorn::KS 

I just saw that I'm having problems with the highlighted text. It's all black, and it won't show the text for search highlighted text. Help please.

---

### Post by edhplus2 on 2011-02-25
The blacked out highlighted text for search results looks like a bug. Here is a bug report/thread at winehq: [http://bugs.winehq.org/show_bug.cgi?id=24998](http://bugs.winehq.org/show_bug.cgi?id=24998)
One person said "If a single search text word appears on it's own line then the highlighting works as expected. If 2 search words appear on the one line they are blacked out"  
so that could be a work around for now, just look for the most narrowly focused word, if possible.  (or remember what you searched for :) Two of the maintainers of the WtLibrary on wine have comments in the thread and at the bottom one of them says he has filed a bug report, so, I guess, stay tuned. 
It must vary from computer to computer or driver to driver, because I don't have that problem.:D

---

### Post by Bcrowes11 on 2011-02-25
So there's no work around?

---

### Post by edhplus2 on 2011-02-25
From what I can tell at that thread, changing the preferences in the F2 menu doesn't affect the background color of searched for text, as it should. Keep an eye on the thread, or maybe post your information there, with some specifics about your hardware, so they know how widespead a problem it is and what it affects. I know next to nothing about hardware and drivers.

---

### Post by Bcrowes11 on 2011-02-25
Thanks. I'll do that. I hope the library 2011 will be natively compatible with ubuntu, don't you?:wink:

---

### Post by edhplus2 on 2011-02-25
Yep, but it could be a lot worse, and if I start comparing operating systems or Linux distributions I'll start a flame war. Suffice it to say I am very happy with this combination. 
Glad I could help, 
-- Ed H

---

### Post by Hedgehog1 on 2011-02-25
> **Bcrowes11 said:**
> Thanks. I'll do that. I hope the library 2011 will be natively compatible with ubuntu, don't you?:wink:
 
Most of our fellow users of the library are using Windows - so I don't expect that.  The few Mac users I know have been asking (very politely, of course), but offering the library in more langauges is a bigger priority.
 
This is good to know it can run in Wine. I was planning to install mine inside my Vbox of Win7 (likely still will).
 
This does mean I can install the library and LibreOffice on an older box with Ubuntu and allow folks to operate for free on a donated machine, and not worry about finding an unsed Windows license.
 
:KS

---

### Post by grahammechanical on 2011-02-25
I installed the WT Library through Wine by first putting the Library CD in the drive and then typing in a terminal winefile. This loads a Windows Explorer type file manager which I use to browse the CD drive and click on setup.exe.

It is also possible to load the WT Library program using wine by giving a command in a terminal. If the program fails to load you get error messages that will help indicate what is going wrong. You will need to study the wine guide for doing this.

Regards.

---

