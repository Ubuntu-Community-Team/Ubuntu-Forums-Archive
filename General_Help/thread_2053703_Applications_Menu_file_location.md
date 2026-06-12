---
title: "Applications Menu file location?"
date: 2012-09-05
forum: General Help
---

### Post by Alan.Brown on 2012-09-05
I have Xubuntu set up so that I get the Applications Menu on Right Click on the Desktop.

I want to modify the menu - so where is the file so that I can edit it?

"Menu Edit" allows me to edit the Applications Menu accessed from the left end of the panel and is not what I want.

TIA

Alan

---

### Post by Toz on 2012-09-05
It should be the same menu. 

Are you using xfdesktop to manage your desktop (instead of nautilus or pcmanfm)?

---

### Post by Alan.Brown on 2012-09-06
Yes - I am using xfdesktop I think.  I know I am using xfwm4.

The menu I get by right clicking has a number of items with the "Applications Menu" at the bottom - eg

Open in New Window
Create Launcher
Create URL Link
...
...
Open Terminal Here
Find in this folder
...
...

I wondered if I can edit this menu - in particular the first item "Open in New Window" which opens Thunar.   I would like to change that to Dolphin or Krusader.

There is really no problem - everything works very well.  I just want to tweak!!

Thanks for your reply

Alan

---

### Post by Toz on 2012-09-06
Sorry, I misunderstood. The Applications menu at the bottom is the same as the menu in the panel.

Unfortunately, no - the rest of those items are hard coded.

You could create a Thunar custom action to open directories in Dolphin.
[LIST=1]
[*]Fire up Thunar.
[*]Edit -> Configure Custom Actions
[*]Click the + to create another action
[*]Set the following:
     [LIST]
[*]Basic Tab
        [LIST]
[*]Name = Open in Dolphin...
[*]          Command = dolphin %n
[*]          Icon = <choose an icon>
[/LIST]
[*]     Appearance Conditions Tab
         [LIST]
[*]Directories = checked
[/LIST]
[/LIST]
[/LIST]

You will then get a "Open in Dolphin..." option when you right-click on a directory.

---

### Post by Alan.Brown on 2012-09-06
Thanks for your help.   I will try what you suggest.  As I said, it is not a problem - just fiddling :)

Alan

---

