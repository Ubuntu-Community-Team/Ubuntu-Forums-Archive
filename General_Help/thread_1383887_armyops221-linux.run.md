---
title: "armyops221-linux.run"
date: 2010-01-17
forum: General Help
---

### Post by robertcoulson on 2010-01-17
Hi..I downloaded "American army" game for Linux (armyops221-linux.run).....How do i install this program...Any help would be appreciated.
Bob

---

### Post by ubudog on 2010-01-17
Write click on the file, go to the permissions tab, check the "Allow executing file as a program" Then go to a terminal and type ```
./pathtofile/armyops221-linux.run
``` and press enter.  Then the install should begin.

---

### Post by robertcoulson on 2010-01-17
Hi..Tried what you said .....see attachment...
Bob

---

### Post by ubudog on 2010-01-17
> **robertcoulson said:**
> Hi..Tried what you said .....see attachment...
Bob

I didn't mean "pathtofile" Instead of "pathtofile" put the directory where the file is located. Example: ./home/user/file

---

### Post by robertcoulson on 2010-01-17
Sorry for being stupid...It is on my desk top right now...So  desktop/file name...??
Bob

---

### Post by ubudog on 2010-01-17
> **robertcoulson said:**
> Sorry for being stupid...It is on my desk top right now...So  desktop/file name...??
Bob

Assuming the file is called armyops221-linux.run, all you have to do after you checked the box I said before is ./Desktop/armyops221-linux.run

---

### Post by ubudog on 2010-01-17
Actually this might be an easier guide: [https://help.ubuntu.com/community/InstallingRunPackage]("https://help.ubuntu.com/community/InstallingRunPackage")

---

### Post by robertcoulson on 2010-01-17
Got this far so far....Don't know what they are asking
Bob

---

### Post by robertcoulson on 2010-01-17
Thanks for trying to help a stupid person Ubudog...I will struggle with that URL...Thanks.
Bob

---

### Post by ubudog on 2010-01-17
Not a problem.  This is what I do in my spare time.  Just press enter on that.  If it gives you an error message then open a terminal and type ```
sudo ./Desktop/armyops221-linux.run
``` enter your password, press enter, and everything should work.

---

### Post by robertcoulson on 2010-01-17
Surprise...It loaded as you said..I see under "applications" a menu called "other"...In there is americanarmy, but I click on it and it will not open...Thanks, I will fiddle a bit more to make it run some how..Thanks ubudog for your patient help.
Bob

---

### Post by ubudog on 2010-01-17
> **robertcoulson said:**
> Surprise...It loaded as you said..I see under "applications" a menu called "other"...In there is americanarmy, but I click on it and it will not open...Thanks, I will fiddle a bit more to make it run some how..Thanks ubudog for your patient help.
Bob

No problem.  Open up the menu editor: System>Preferences>Main Menu, click on Other, click on americanarmy, and click on Properties.  What does it say after "Command"?

---

### Post by robertcoulson on 2010-01-17
Here is what I get....
Bob

---

### Post by ubudog on 2010-01-17
There should only be one slash after the first armyops.  Here is what should be after the "Command":/usr/local/games/armyops/armyops

That might work.  Hope that helps! ;)

---

### Post by robertcoulson on 2010-01-17
Did what you said ubudog...but to no avail...Hey, thanks for your help anyway...I won't take up your valuable time anymore...Just going to delete it when I find out how..
Thanks again, Bob

---

### Post by ubudog on 2010-01-17
> **robertcoulson said:**
> Did what you said ubudog...but to no avail...Hey, thanks for your help anyway...I won't take up your valuable time anymore...Just going to delete it when I find out how..
Thanks again, Bob

You could just delete all the files.  Open up the file browser, go on Filesystem, and search for armyops221.  Then once it's done highlight everything about that game and delete it.

---

### Post by robertcoulson on 2010-01-17
Could not find all the files..Just deleted what I had originally downloaded and delete the "other" menu...At least I won't have to look at it (ha,ha)
Bob

---

### Post by ubudog on 2010-01-17
> **robertcoulson said:**
> Could not find all the files..Just deleted what I had originally downloaded and delete the "other" menu...At least I won't have to look at it (ha,ha)
Bob

Oh well, good luck with linux. :o

---

