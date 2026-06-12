---
title: "Microsoft Office 2000 Product Key Force Shutdown"
date: 2010-01-10
forum: General Help
---

### Post by Scorchgid on 2010-01-10
Okay so here my problem, I installed office 2000 CD using wine, I did this on Ubuntu net-book remix on a NC10 using a networked CD drive.

So the installation went okay, I then came to using the software, word opened and promoted me for my product key, which I entered correctly the window disappeared for a second then repaired, I entered the key again but then this caused the whole program to shut down, I have tried repairing it , reinstalling it all apart from uninstalling and reinstalling it. Which I have tried and subsequently failed 
any suggestions

Also please, please please. Don't recommend Open Office, I've tired it and I don't like it. If your opinion is this please take it else where.

Many thanks

Scorchgid

Ps Apologies if this is in the wrong forum.

Right I got it to work, so for any looking for the solutions simply go to /home/(username)/.wine/system.reg and change the user name and the organisation either delete it or enter something, I entered my user name but I left the organisation  blank but I left the quote marks that were there. Save it and the product code thingy should not appear again.

---

### Post by bodhi.zazen on 2010-01-10
Wine is not so easy to use.

My advice is to either :

1. Use OpenOffice (if at all possible). Open office works with many if not all Windows Office files, and you can run OOO on Windows. You will simply have an easier time if you are able to transitino to OOO.

I know that is not what you want to hear, but it is still hands down the best optionas OOO is cross platform and more compatible then Office. Although the transition can take time, it is rare OOO lacks some essential feature, although it does happen, the vast majority of people the limitations of OOO are "self imposed".

2. If you "must have" a windows application, you will almost certainly find VirtualBox is easier (and more reliable) then wine. Install Virtualbox then install windows and MS Office in Virtualbox.

---

### Post by mk1w86 on 2010-01-10
> 2. If you "must have" a windows application, you will almost certainly find VirtualBox is easier (and more reliable) then wine. Install Virtualbox then install windows and MS Office in Virtualbox.

I don't think VirtualBox would run very well on an Atom CPU. 

> Also please, please please. Don't recommend Open Office, I've tired it and I don't like it. If your opinion is this please take it else where.

What exactly is it about OpenOffice you do not like?  You could also try AbiWord and Gnumeric which are much lighter than OpenOffice and will probably run faster on your netbook. :D

---

### Post by Ugluk on 2010-01-10
I thought Office 2000 asks for CD-Key only during install?
Also, try to run Word from terminal and capture the Wine output. Then submit a Wine bug.

---

### Post by bodhi.zazen on 2010-01-10
> **mk1w86 said:**
> I don't think VirtualBox would run very well on an Atom CPU. 

It runs just fine on an atom CPU, although it is slow, but then again so does everything else. I agree that in general the atom is underpowered , but it serves it's purpose (small size, portable, less then a full laptop).

---

### Post by Scorchgid on 2010-01-11
> **Ugluk said:**
> I thought Office 2000 asks for CD-Key only during install?
Also, try to run Word from terminal and capture the Wine output. Then submit a Wine bug.

Okay bear in mind I have no idea how to do that, but I will give it a search, although when your next on please clarify how to do this.

It did and then did something funny, I can't explain what but it froze so I had to abort the installation, it did not abort correctly, however I do remember entering the code at the start of the installation.
Wine won't let me uninstall it or rather it does, but then doesn't (it runs the uninstaller but does not uninstall the files, believe me I would love too uninstall it and start again but I don't know how. Okay please don't recommend a wipe of the drive , I just got the computer the way I wanted it and had to get a friend to clear up the last mess I made.

So to summarise, I'd first like to get rid of the existing word and then to reinstall it, without wiping my drive, is it possible to delete office from the drive. will that uninstall it. Also I have run the uninstaller from wine with no success.

Many thanks

Open office, I dunno my and him didn't get off to a good start we had some problems with fonts here and there and he didn't have a good dress sense, word had a bit of a better dress sense and could work well with his younger brothers. In the end we found although we could we didn't like working together.

---

### Post by Scorchgid on 2010-01-24
Right I got it to work, so for any looking for the solutions simply go to /home/(username)/.wine/system.reg and change the user name and the organisation either delete it or enter something, I entered my user name but I left the organisation  blank but I left the quote marks that were there. Save it and the product code thingy should not appear again.

---

### Post by malibusurfer2 on 2010-06-10
Some of us poor souls need to use MS Office. I have Access database applications and run Office 2000 Pro under Windows in VirtualBox and standalone using Wine (CrossOver Linux). I am currently trying to install on an MSI netbook - no CD drive. Ubuntu is wonderful, but sometimes we need to run Windows only applications (Turbo Tax, Quicken,???).

---

### Post by bodhi.zazen on 2010-06-10
> **malibusurfer2 said:**
> Some of us poor souls need to use M$ Office. I have Access database applications and run Office 2000 Pro under Windows in VirtualBox and standalone using Wine (CrossOver Linux). I am currently trying to install on an MSI netbook - no CD drive. Ubuntu is wonderful, but sometimes we need to run Windows only applications (Turbo Tax, Quicken,???).

Yep, add voice recognition to the list of windows only =(

---

### Post by Sef on 2010-06-10
Depending on your needs AbiWord may do the word processing for you.  It is much improved and much more compatible with ms word now.  Just download it from the respositories.

---

