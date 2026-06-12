---
title: "Panel autohide breaks taskbar in 11.04"
date: 2011-07-01
forum: General Help
---

### Post by BobLloyd on 2011-07-01
Ubuntu 11.04 running on Asus X58C.

**Defect:**
When setting a panel to autohide, after moving it to the bottom of the screen, I found that it was not completely hidden but persisted as a flickering line of a few pixels height.

The functionality of the task bar was completely broken.  Clicking would not launch applications and there was no way to access Applications/Places/Systems.  Since nothing could be launched, the system was broken.  Although it is possible to change the gconf settings using gconf-editor, this is of no use if you cannot even launch the terminal.  It was not even possible to use Alt-F2 to access a terminal session.

**Fix:**
1. Boot the system using an Ubuntu installation disk and opt to try out Ubuntu.

2. Open Computer from Places and click on the hard drive icon which will mount it and make it accessible.

3. Open a terminal session from Applications/Terminal and run "sudo gedit" (without quotes).  This will open up the text editor with an empty file.

The functionality of the Panel is controlled by settings in XML files in the hidden .gconf folder in your home folder. There are many files all called %gconf.xml and their location determines their content so we will navigate to the appropriate xml file and change the setting which controls the auto_hide feature.

4. Click the Open button in gedit and then press Ctrl-h to show hidden files.

5. Navigate to the folder called:
.gconf/apps/panel/toplevels/top_panel_screen0

(NB - even if you have moved the panel from the top to the bottom, it is still the top_panel_screen0 folder.)

6. You will see a file called %gconf.xml. Click on it, then click on Open.

7. Towards the bottom of the file, you will find an entry with the name "auto_hide" which contains a line similar to this (the mtime entry will probably be different but it doesn't matter):

<entry name="auto_hide" mtime="1309447780" schema="/schemas/apps/panel/toplevels/auto_hide" type="bool" value="true"/>

Change the word "true" to "false" and save the file.  

8. Close gedit and reboot the system.

In my case, that was enough to get the machine back to working state. I can't provide support for others trying to solve this problem so this solution is "as is".  If it works for you, fine. If not, then please post other suggestions which might help others.

---

### Post by cweigle on 2012-03-10
Ubuntu 10.04 on old Dell Inspiron 2200 laptop

This was hugely helpful to me, having the same problem in the 10.04 LTS release. 

This is a very well written solution, but as a relatively unsophisticated user I missed an important unstated direction. Step 5 should have directed me to open the file as directed, but starting in the home folder of the user whose account I had screwed up with the autohide problem. Obvious to many, I'm sure, but took me a while to figure out what I was doing wrong.

As soon as I was back in the system, I added a new rescue user with admin rights so that, if I do something like this again, I can fix it without needing to boot from a CD.

---

