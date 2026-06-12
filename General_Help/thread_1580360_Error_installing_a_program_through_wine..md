---
title: "Error installing a program through wine."
date: 2010-09-23
forum: General Help
---

### Post by Danger Fox on 2010-09-23
I recently got a new netbook and the first thing I did was install ubuntu along side the XP install. The problem I'm running into right now is when I try to install a statistics program that I need for class I get an error. There is a popup labeled RegUtil with the error "Run-time error '5': Invalid procedure call or argument" and in the terminal window there is the message "wine: cannot find L"C:\\windows\\system32\\netsh.exe." Can anyone help me figure out what this error is and fix it?

---

### Post by TuxLyn on 2010-09-23
It looks like you are missing some runtime files for your stats program. It might be .NET framework.

---

### Post by pedro_orange on 2010-09-23
> **Danger Fox said:**
> I recently got a new netbook and the first thing I did was install ubuntu along side the XP install. The problem I'm running into right now is when I try to install a statistics program that I need for class I get an error. There is a popup labeled RegUtil with the error "Run-time error '5': Invalid procedure call or argument" and in the terminal window there is the message "wine: cannot find L"C:\\windows\\system32\\netsh.exe." Can anyone help me figure out what this error is and fix it?

The application is telling you it can't find the application netsh.exe in C:\windows\system32.

If you have a look in ~/.wine/, you will be in what you know as the C:\ drive. Look for your netsh.exe in the windows\system32 folder. It's probably not there. 
If it there, you might not have permissions to run it. Try running the application as a super user or something. 

My guess is it is not there. You will probably have to install it.

Keep us posted.

---

### Post by Danger Fox on 2010-09-23
Thanks for the quick response! I looked in the wine folder in system32 and found that the file netsh.exe is not there. I'm rather inexperienced with wine, how would I go about installing it?

---

### Post by pedro_orange on 2010-09-23
You might be best off getting a copy of netsh.exe from a Windows installation, and dumping it in the folder I mentioned previously in your Linux installation.

---

### Post by sydbat on 2010-09-23
To the OP - if you have XP as the dual boot, try installing the program in XP, then boot into Ubuntu and run it from there. In the past when I dual booted XP, I was able to run many (not all of course) Windows apps from the NTFS partition by opening them with WINE. Might work, and save HDD space.

---

### Post by Danger Fox on 2010-09-23
So, I coppied the file netsh.exe right from the Windows directory and whenever I try to install it now I get the error that netsh.exe has encountered an error and needs to close. Any idea on why it would be doing that? My plan right now is that if I can get everything I need running in Ubuntu, then I can get rid of the Windows partition. If I can't get this to work then I will definately try your suggestion sydbat.

---

### Post by pedro_orange on 2010-09-23
Okay, please refer to this Microsoft knowledgebase article: 

[http://support.microsoft.com/kb/242468](http://support.microsoft.com/kb/242468)

If you check the bottom of the page, you will see it has a number of dependencies on DLLs. You may well be better off running the application from your Windows partition. 

Since we don't know what the application is or it does, I can't really suggest any Linux-friendly alternatives or think of a way to get the same functionality on Linux.

---

### Post by Danger Fox on 2010-09-23
Thanks for the help that you all were able to give. It looks like I may just have to run it in Windows. The program is for taking tests and quizes for a class I'm in, so there really is no alternative since I had to purchase a license for this particular one, sadly.

---

### Post by pedro_orange on 2010-09-23
> **Danger Fox said:**
> Thanks for the help that you all were able to give. It looks like I may just have to run it in Windows. The program is for taking tests and quizes for a class I'm in, so there really is no alternative since I had to purchase a license for this particular one, sadly.

You could always run this application in a Virtual machine on the Ubuntu box.

---

### Post by Mark Phelps on 2010-09-23
In future, you could save yourself a lot of time and grief if you first go to the WineHQ site linked below and do a search on the app you want to run:

[http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true")

Unless the ratings are Gold or better, or if the app is not listed, you're essentially wasting your time with Wine and that app.

---

### Post by Kaboom3009 on 2011-12-05
netsh.exe is microsofts network sharing program that registers programs for outside interaction with programs over the internet and on local networks. It is NOT a full open share but a microsoft hack to bypass the full open sharing to allow limited trusted sharing for trusted aps. A large number of programs like VOIP stuff (dolby axon) require registering themselves with this file to allow 2 way open communication above and beyond the basic internet or LAN allowed protocols to pass program specific data. A linux comparison would most likely be giving a program super user status so it can access all of its functionality that is programmed OUTSIDE of the normal constraints for one reason or another.

---

