---
title: "how to copy my bookmarks inside Firefox"
date: 2009-12-09
forum: General Help
---

### Post by flywelder on 2009-12-09
I am currently using Ubuntu version 7.4, but I want to install the latest version.  I use Firefox for my web browser.  

Before I do the new installation I want to make sure I will still have my favorites/bookmark websites.  Will they still be there or do I need to copy them?  If I need to copy them how do I do that so I can reinstall them when I have installed the latest version of Ubuntu?

---

### Post by MelDJ on 2009-12-09
what version of firefox? if it is 3.5, go to history-show all history. at the sidebar, select all bookmarks. then select import and backup and press backup

---

### Post by lyall on 2009-12-09
the bookmark file is in the /home/username/.mozilla/firefox/o9kkuq12.default
the look for the bookmarks.html file
that is for Foxfire 3.5 it should be in the same location for any Foxfire

you can save this file any to CD flash drive or to s spare hard drive 
good luck and have some fun learning

---

### Post by john newbuntu on 2009-12-10
In firefox, you have the Bookmarks->organize bookmarks menu.  You would then go to import/export menu and then save your bookmarks in an html format.
In general, before you perform upgrade, save your entire home directory (using any command that you are familiar with like cp, rsync, tar etc.) on a flash drive or other device just in case.

---

### Post by Silvernail on 2009-12-15
I too need this information:

I have saved the bookmarks.html to an external drive.
Install Jackalope.
Copy bookmarks.html back to computer in home directory
Click on firefox
Click on file
Click on import
Get message not bookmark or address file could be found.

Physically copied bookmarks.html to .mozilla/firefox/blah blah.default/bookmarks.html

Does not show up in 'firefox' bookmarks.

This is on my laptop.  I have a desktop with exactly the same installation and all upgrades that does not  have this problem.

What else should I look for or do?
TIA
Dave

---

### Post by ST3ALTHPSYCH0 on 2009-12-15
If you copy the entire contents of  /home/username/.mozilla/firefox/xxxxxxxx.default into the new install's  /home/username/.mozilla/firefox/xxxxxx.default folder you'll get your bookmarks, passwords, cookies, history....everything.

---

