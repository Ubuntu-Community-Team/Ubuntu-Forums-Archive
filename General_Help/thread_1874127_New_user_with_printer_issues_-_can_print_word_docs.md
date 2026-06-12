---
title: "New user with printer issues - can print word docs not PDFs."
date: 2011-11-02
forum: General Help
---

### Post by Rebecski on 2011-11-02
Hi All,
Sorry if this is a daft question. I installed Ubuntu a couple of days ago as a new to Linux user and I'm just getting to grips with it. 
I'm having a bit of an issue with my printer which won't print PDF or powerpoint, but will print word documents and excel (I mean the open source equivalent of these).
It prints test pages fine and I downloaded all the recommended drivers.
The printer is a Canon iP2700.
Can anyone help?
Thanks. :)

---

### Post by Paddy Landau on 2011-11-02
Could you tell us more information, please. What errors do you get? Does the print job just vanish? Or do you get an error message? Does the print dialogue simply not appear when you try to print? When you try to print, which printer do you select?

---

### Post by Rebecski on 2011-11-02
Hi, thanks for your reply. It's says it's printing, and then nothing happens. I clicked on the printer log thing, and it says that it is processing, then ok but nothing actually happens. I am selecting the canon printer when I print. I don't really know what else to say about it.
Think I might try downloading another PDF reader (like Adobe) and see if I can print with that though I would like to know what I'm doing wrong with this one.
:)

---

### Post by Paddy Landau on 2011-11-02
Well, I'm sorry, this is not a problem I've come across before.

I'll run through a couple of obvious things, just in case. You don't say which version of Ubuntu you have; I presume you have 11.04 or 11.10.

[LIST]
[*]Open your *Printing* application.
[*]You should see your printer as an icon.
[*]Is it the default? If you're not sure, right-click: Can you select *Set As Default*?
[LIST]
[*]If you cannot, it's already default.
[*]If you can, it is not default; so make it default, log out and in again, and try printing again.
[/LIST]
 
[*]Right-click the icon again and select *View Print Queue*. Are your old jobs listed? If they are, can you do anything with them?
[/LIST]
When you try to print from an application that does not work (e.g. Evince, which is the default PDF viewer), are you making sure that you have chosen the correct printer? Run through the various options on the print dialogue and check that everything is correct; e.g. have you chosen the correct page size?

Here's something else.

[LIST=1]
[*]Reboot.
[LIST]
[*]Open an application that works; print a page.
[*]Then open an application that doesn't work; try to print a page.
[/LIST]
 
[*]Reboot.
[LIST]
[*]Open an application that doesn't work; try to print a page.
[*]Then open an application that works; print a page.
[/LIST]
 
[/LIST]
Was there any difference between point 1 and 2?

---

### Post by Mark Phelps on 2011-11-03
Check in synaptic to see if CUPS-PDF is installed.  If you're running 11.10, you'll have to install Synaptic first.  I think that will allow you to then print PDF files.

---

### Post by nodjoim on 2012-05-02
I recently have a problem with printing PDF's;  all other file types work fine. I am running 11.10. The pdf jobs remain in the print queue indicated as erroneous. Also, the printing effort even leaves the printer (a professional Xerox laser printer) in an error state which requires it to be reset!


> **Paddy Landau said:**
> Well, I'm sorry, this is not a problem I've come across before.

I'll run through a couple of obvious things, just in case. You don't say which version of Ubuntu you have; I presume you have 11.04 or 11.10.

[LIST]
[*]Open your *Printing* application.
[*]You should see your printer as an icon.
[*]Is it the default? If you're not sure, right-click: Can you select *Set As Default*?
[LIST]
[*]If you cannot, it's already default.
[*]If you can, it is not default; so make it default, log out and in again, and try printing again.
[/LIST]
 
[*]Right-click the icon again and select *View Print Queue*. Are your old jobs listed? If they are, can you do anything with them?
[/LIST]
When you try to print from an application that does not work (e.g. Evince, which is the default PDF viewer), are you making sure that you have chosen the correct printer? Run through the various options on the print dialogue and check that everything is correct; e.g. have you chosen the correct page size?

Here's something else.

[LIST=1]
[*]Reboot.
[LIST]
[*]Open an application that works; print a page.
[*]Then open an application that doesn't work; try to print a page.
[/LIST]
 
[*]Reboot.
[LIST]
[*]Open an application that doesn't work; try to print a page.
[*]Then open an application that works; print a page.
[/LIST]
 
[/LIST]
Was there any difference between point 1 and 2?

---

