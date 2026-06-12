---
title: "PLEASE HELP!!! software sources"
date: 2011-01-11
forum: General Help
---

### Post by Niks10. on 2011-01-11
Hello im new to ubuntu.
I use ubuntu 10.10 and i wanted to install wine1.3.
But software sources asks me a cd.
I unchecked the ,,Installable from CD-ROM/DVD,, box already but it asks me the same everytime. 
Im disappointed.

---

### Post by Quackers on 2011-01-11
Welcome to UF :-)
How are you trying to install it? Software Centre or Synaptic or some other method?

---

### Post by Niks10. on 2011-01-11
You think from what programm im trying installing it?

---

### Post by Quackers on 2011-01-11
I mean are you trying to install it from a file you have downloaded from a website, or are you using Synaptic Package Manager, or Software Centre from within Ubuntu.

---

### Post by I'mGeorge on 2011-01-11
I think you have to add some proper Ubuntu servers in your sources.list 

As root do gedit /etc/apt/sources.list and make sure the lines that refer to your cd rom as a source are marked as inactive, which means there must be the # sign at the beginning of the lines.

---

### Post by Niks10. on 2011-01-11
Im totaly new to ubuntu.
Cloud you explain it what i have to do?
like this  
System>Preferences..........
I use ubuntu 10.10
If you cloud give me good instruction for WINE (better than these in winehq website ) that would be a lot better

---

### Post by Quackers on 2011-01-11
System > Admin > Synaptic Package Manager
In the search box enter "wine" and see what comes up in the main window.
If what you want is there, right-click on it and select "mark for installation".
Then click the green tick in the toolbar to apply the change.
Then watch it install :-)

---

### Post by Niks10. on 2011-01-11
Thanks! :) :) :) i think it worked 

But i have to open an installer or game *.exe *trough wine?

---

### Post by Quackers on 2011-01-11
> **Niks10. said:**
> Thanks! :) :) :) i think it worked 

But i have to open an installer or game *.exe *trough wine?

You're welcome :-)
And, yes, you should open .exe's through Wine afaik. Some games don't do too well though, as I understand it :-(

---

