---
title: "Nautilus won't remember default action"
date: 2010-05-28
forum: General Help
---

### Post by zerubbabel on 2010-05-28
I did a fresh install of 10.04 a couple of weeks ago, and all seemed well, but lately when I double-click on, say, an OpenOffice (.odt) file in Nautilus, I get the following message:
[INDENT]The file '/home/zerubbabel/Documents/Teachings/Queue/2010.05.15-A02.odt' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.[/INDENT]
(The pop-up window title reads: "Blocked: wine start /unix") 
I've repeatedly set the "Open with..." and checked "Remember this application...", but it doesn't "stick".

---

### Post by mc4man on 2010-05-28
Not sure why this silly executable bit deal is getting applied to an .odt file, but if you wish the change/set a default (d. left click) action then do so with
right click - **properties** - open with...

---

### Post by zerubbabel on 2010-05-29
Already tried that numerous times, but it doesn't "stick"...

---

### Post by alem189 on 2010-05-29
I think the "wine start /unix" bit means that Wine is trying to open it... Have you checked that it isn't set to open .odt files? I don't know how that could have happened, and I don't know much about Wine, but that might be the reason why is isn't sticking. I might be totally interpreting that message there wrong though...

---

### Post by zerubbabel on 2010-05-29
Well, actually, when I change the "Open with..." in the file properties, it does stick. Before I had done it just by right clicking on the file and choosing "Open with..." from the pop-up menu, and that didn't stick. 

Why it associated the .odt files with Wine I have no idea.

---

### Post by cscj01 on 2010-06-13
I am running Lucid with all updates applied to date.  I am having a similar problem with Nautilus and files with a txt extension.  If I double click the file icon, nothing happens.  If I right click the file icon and choose Open with Other Application and select gedit, the file opens in gedit.  When I right click, choose Properties, and select the Open With tab, gedit is the application specified.

I started Nautilus from a terminal using sudo.  When I double click the file, I get a message asking me if I want to execute or display the file.  I select Display, and the file is opened in gedit.

I have tried resetting the application on the Open With tab both as root and my user id.  This does not change behavior in either case.

Any ideas as to why I cannot open "plain text documents" from Nautilus by double clicking even though the Properties tab says I can?

By the way, Others shows read and write permissions on the Permissions tab, and Execute is checked.

---

