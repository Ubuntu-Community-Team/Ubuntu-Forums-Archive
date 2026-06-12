---
title: "Lucid Save As/Open dialog focus issue"
date: 2010-05-01
forum: General Help
---

### Post by Exp HP on 2010-05-01
So I upgraded from Karmic to Lucid today.

Like in earlier versions of Ubuntu, typing into the standard Open and Save As dialogs after bringing one up in Ubuntu 10.4 will type into the Location/Name field.

Like in earlier versions of Ubuntu (or, at least, I think it was this way), if you click somewhere in the main file pane, focus is placed there, and all further typing is redirected to a pop-up search box.

*Unlike in earlier versions of Ubuntu, if you move to a new folder by double-clicking one in the main file pane, focus does not return to the Location/Name field (even though the file name typed into the field will be auto-highlighted)*. Unless you click back into the Location/Name field, anything you type will go into the pop-up search.


I find this last bit of behavior undesirable, at least in the Save As dialog.    It's a great loss in intuitiveness. After browsing into a folder, any typing I do is likely intended to be the file name.  Actually, I might even go so far as to call the current behavior a cosmetic bug (since it highlights/selects the file name without returning focus to it).
How do I change it back to the behavior in Karmic?


**EDIT:**  In case I was not clear, this applies to the operating system's standard open/save dialog *that all programs use by default.*
To clarify my problem, when you are in such a dialog and double click on a  folder to open it, then if you start typing, you will end up typing into a search box.
*This was not the behavior in Karmic*. In 9.10, it would've let you type right into  the file name, because it used to return focus to the name field after  opening a folder.
I want that behavior back because it was intuitive.
*(this was copied from a later post)*

---

### Post by Exp HP on 2010-05-02
[shameless bump]

---

### Post by Exp HP on 2010-05-02
As I've fallen to page 3, bump again, I s'pose.

---

### Post by llamabr on 2010-05-02
are you asking about openoffice?  if you get no answer here (i don't quite understand your question) you might take it to their forum.  they're quite good at answering the esoterica about ooo.

---

### Post by Exp HP on 2010-05-02
It affects **the standard open/save dialog**. Yes, it affects OOo, but it also affects gedit, The GIMP, and even gnome-terminal (File>>Save Contents).  It affects every program except a select few like Blender which has its own built-in open/save widget integrated into the interface.

I'm beginning to wonder... are other people not experiencing this problem?


To clarify my problem, when you are in the dialog and double click on a folder to open it, then if you start typing, you will end up typing into the search box.
*This was not the behavior in Karmic*. In 9.10, it would've let you type right into the file name, because it used to return focus to the name field after opening a folder.
I want that behavior back because it was intuitive.

---

### Post by Exp HP on 2010-05-08
5+ days and still nothing?  Part of me wants to just let this go, because if I plan ahead and enter the desired name before I enter any folders, then as long as I don't click on any files, the desired name will be there and I can just press enter/click OK when I'm done navigating.

...but the rest of me wishes this awkward change in the GUI could just be changed back.  And I still think that it's a bug, because the text in the name field should not be auto-selected unless typing will go into the name field.

So... verbose BUMP.

---

### Post by magnumjones on 2010-05-17
I'm on board.  This thing drives me crazy.

---

### Post by charrah on 2010-06-06
This has driven me nuts ever since I started using Ubuntu. Is there a bug report for this? Maybe it counts as a papercut and could be fixed in time for Maverick

---

### Post by bogdarnet on 2011-01-17
I've noticed this recently as well.  Odd thing is, I think it started recently (don't remember it being a problem before!) -- anyone figured it out yet?

---

### Post by MorayJ on 2011-10-29
I had a feeling that this had been a problem with Gnome for a while and it's very irritating.

More irritating to find that Unity has kept it on.

I'm thinking we're talking about the same problem, but this is the only thread on the first 3 of google that has it, so my description might be off.

When I do 'save as', if I then change to another folder than the one that 'save as' defaulted to, my next bit of typing goes into the search box for filtering the files in that folder.

But I'm still trying to save my file and the next thing I always type is the filename I want to save it as (after all, I've just switched to the folder I want to save in).

Unfortunately, this now gets typed pointlessly in the filter field.

So, seconding/thirding this, or hoping someone may have an answer..

---

### Post by lns on 2012-02-17
I just found this thread because I was looking for a solution to this very long standing annoyance - only this is the case in Debian, too (which I use, with Gnome3 no less). So it's a general GTK issue which can be configured I would assume...but I can't find anything online after a half an hour search frenzy (just confirmations).

There should really be a gconf setting for this, at least.

---

