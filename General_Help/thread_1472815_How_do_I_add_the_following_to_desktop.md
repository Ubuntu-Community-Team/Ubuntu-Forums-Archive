---
title: "How do I add the following to desktop?"
date: 2010-05-04
forum: General Help
---

### Post by joelw135 on 2010-05-04
I would like to add the home folder, network, trash to desktop, how do I do this?

---

### Post by garvinrick4 on 2010-05-04
> **joelw135 said:**
> I would like to add the home folder, network, trash to desktop, how do I do this?
Lets go Alt/F2 and when it opens type gconf-editor and click run.
Go to Apps to Nautilus to Desktop and check any box you want for what you want on desktop.

gconf-editor can be installed in Applications/System tools in main drop down menu. Open 
a terminal and Code:

sudo apt-get install gconf-editor

---

### Post by louis--taylor on 2010-05-04
Install Ubuntu tweak for easy adjustment of these sort of things, and tick the checkboxes you want.
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by WorMzy on 2010-05-04
Press Alt+F2 ro bring up the run command. Type 'gconf-editor' and hit Run. Browse to /apps/nautilus/desktop and check the options you'd like.

---

### Post by Calash on 2010-05-04
You have a couple of options

If you do not mind installing external applications you can install ubuntu-tweak.  It is a very user friendly configuration application that includes what you are looking for

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

Your other option is to open a terminal and type the following

```

gconf-editor

```

On the left browse the folder tree as follows

>apps>nautilus>desktop

In here you will see several items.  Check the following

home_icon_visible
network_icon_visible
trash_icon_visible

That will get you the setup you want


There is a full command line way to do this as well, however I do not know it off the top of my head so I will defer that to another poster.

---

### Post by joelw135 on 2010-05-04
> **garvinrick4 said:**
> Lets go Alt/F2 and when it opens type gconf-editor and click run.
Go to Apps to Nautilus to Preferences and check any box you want for what you want on desktop.

gconf-editor can be installed in Applications/System tools in main drop down menu. Open 
a terminal and Code:

sudo apt-get install gconf-editor

Thank you and everyone for the quick reply, have it all working now.

---

