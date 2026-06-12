---
title: "How to edit Natilus right context menu?"
date: 2010-07-19
forum: General Help
---

### Post by etdsbastar on 2010-07-19
Hello there,

I want to edit/remove some items in my NAUTILUS Right-Click Context menu which appears on right clicking on nautilus window (blank area). How to do that?

Please help.

---

### Post by Vaphell on 2010-07-19
what exactly would you like to achieve?

---

### Post by dino99 on 2010-07-19
right click on top panel "applications" and select "edit menu"

---

### Post by etdsbastar on 2010-07-19
> **Vaphell said:**
> what exactly would you like to achieve?

Please check the screenshot, the right click menu, i want to change/add some items there. How can i do this.

---

### Post by Vaphell on 2010-07-19
adding entries is possible via addons and i doubt there is such fancy menu editor like in case of system menus.
I asked what specifically you'd like to add/remove to the context menu itself.

edit:
install nautilus-actions (sudo apt-get install nautilus-actions) - it provides a tool to add custom entries to context menu, maybe it can't do everything but it's a nice start

example of that plugin in action:
[http://www.prash-babu.com/2009/11/how-to-enqueue-mp3-file-to-totem-in.html](http://www.prash-babu.com/2009/11/how-to-enqueue-mp3-file-to-totem-in.html)

---

### Post by etdsbastar on 2010-07-19
> **Vaphell said:**
> adding entries is possible via addons and i doubt there is such fancy menu editor like in case of system menus.
I asked what specifically you'd like to add/remove to the context menu itself.

edit:
install nautilus-actions (sudo apt-get install nautilus-actions) - it provides a tool to add custom entries to context menu, maybe it can't do everything but it's a nice start...

Actually I am already having nautilus actions installed. I want to remove some actions there. I want to know where does nautilus stores all these context-menu informations.

---

### Post by etdsbastar on 2010-07-20
bumping... no reply from very long time...

---

### Post by ankspo71 on 2010-07-20
Hi,
According the nautilus actions site, these configurations are imported into in gnome's configuration settings. Or at least the 'default schema' is.
[http://www.grumz.net/index.php?q=node/7](http://www.grumz.net/index.php?q=node/7)
So try launching the Gnome Configuration Editor by pressing Alt+F2 then typing gconf-editor. Once it opens, browse or search for the nautilus actions settings.

Other configurations are stored in:
~/.nautilus-actions  (a hidden folder in your home directory)
/usr/share/nautilus-actions (the folder used for all users)

Hope this helps.

---

### Post by Vaphell on 2010-07-20
my bet is it's either hardcoded (basic options) or buried somewhere among the mime type configs and .desktop files configuring apps (filetype related options). In user/share/nautilus you can find all configs for all parts of GUI but context menu is not there. Maybe there is something in countless gnome config files, but good luck finding that :/

---

### Post by etdsbastar on 2010-07-20
> **Vaphell said:**
> my bet is it's either hardcoded (basic options) or buried somewhere among the mime type configs and .desktop files configuring apps (filetype related options). In user/share/nautilus you can find all configs for all parts of GUI but context menu is not there. Maybe there is something in countless gnome config files, but good luck finding that :/

Thanks for your help Vaphell and all other who have helped me. I think this problem cannot be solved at once,,,, lets try all of us... If anyone gets the solution, will post it here... Ok

Good luck to all of you...

---

### Post by satish_j on 2010-12-01
Hi,did you get the file that stores the menu items for Nautilus context menu??

---

### Post by etdsbastar on 2010-12-01
Hello friend, 

I got the answer and thanks for your reply.

---

### Post by satish_j on 2010-12-01
> **etdsbastar said:**
> Hello friend, 

I got the answer and thanks for your reply.

Could you pls share the solution with forum??

---

### Post by dvdbrnds on 2011-03-04
Im Struggling to find this myself...

---

### Post by jayboe on 2011-11-28
UBUNTU 10.04 / FEDORA 13
I know it's a little late in the game, but this is a thread that I came across during my search for "How to".
Forget nautilus-actions for customizing built in menu selections. Works great for creating new ones though.
Ok, so here it is,
You're gonna have to get a little dirty in a .xml file

First  things first. If you're gonna make changes to a system file it is best  to make a backup of the file before you get started, and you must be  root. I like to work from the directory where the project is so let's  get started by changing to that directory.

[COLOR=DarkRed]cd /usr/share/nautilus/ui[/COLOR]

Now let's get to work.

[COLOR=DarkRed] sudo cp nautilus-directory-view-ui.xml nautilus-directory-view-ui.xml.bak[/COLOR]

Now use your editor of choice e.g. (vi,nano, or a gui like gedit) Me, I like nano to do my bidding. ;-)

[COLOR=DarkRed]nano nautilus-directory-view-ui.xml[/COLOR]

Here  is a sample block of xml code from my system after the adjustment. I  figure the easiest way to edit the file without deleting anything like I  read in another post is to simply comment out the crap that you don't  want.
Comments in xml must be preceded by <!-- and ended with -->
With  that being said take notice at the beginning and end of this block  where I placed the comment indicators. On this block I started at the  "placeholder" and ended on the "placeholder", but it is not limited to commenting there. You can pick and choose "menuitem", too. By doing  it this way with the comments it is also easy to just go back and  un-comment what you commented to undo changes verses the .bak approach  mentioned above which is more secure.

...............<!--placeholder name="Clipboard Actions">
........................<menuitem name="Cut" action="
........................<menuitem name="Copy" action="Copy"/>
........................<menuitem name="Paste" action="Paste"/>
................</placeholder-->
.................<!--placeholder name="Select Items">
.................<menuitem name="Select All" action="Select All"/>
.................<menuitem name="Select Pattern" action="Select Pattern"/>
.................<menuitem name="Invert Selection" action="Invert Selection"/>
.................</placeholder-->
................<placeholder name="File Items Placeholder">
........................<!--menuitem name="Duplicate" action="Duplicate"/-->
........................<!--menuitem name="Create Link" action="Create Link"/-->
........................<menuitem name="Rename" action="Rename"/>
........................<!--menu action="CopyToMenu">
................................<menuitem name="Copy to next pane" action="Copy to next pane"/>
................................<menuitem name="Copy to Home" action="Copy to Home"/>
................................<menuitem name="Copy to Desktop" action="Copy to Desktop"/>
........................</menu>
........................<menu action="MoveToMenu">
................................<menuitem name="Move to next pane" action="Move to next pane"/>
................................<menuitem name="Copy to Home" action="Move to Home"/>
................................<menuitem name="Copy to Desktop" action="Move to Desktop"/>
.........................</menu-->
....................</placeholder>
.................<!--placeholder name="Dangerous File Items Placeholder">
........................<menuitem name="Trash" action="Trash"/>
........................<menuitem name="Delete" action="Delete"/>
........................<menuitem name="Restore From Trash" action="Restore From Trash"/>
....................</placeholder-->

Run this command to restart nautilus if you feel so inclined.

[COLOR=DarkRed]nautilus -q[/COLOR]

COMMAND SUMMARY

[COLOR=DarkRed]cd /usr/share/nautilus/ui
sudo cp nautilus-directory-view-ui.xml nautilus-directory-view-ui.xml.bak
nano nautilus-directory-view-ui.xml
nautilus -q[/COLOR]

So,  now if you make a boo-boo, you can always run this next set of  commands  from within the /usr/share/nautilus/ui directory and then  start the  process over. That is assuming you went with the file backup.

[COLOR=DarkRed]rm -rf nautilus-directory-view-ui.xml
mv nautilus-directory-view-ui.xml.bak nautilus-directory-view-ui.xml[/COLOR]

To add custom commands back to the context menus, you can install;

[COLOR=DarkRed]apt-get install nautilus-actions[/COLOR]        via ubuntu
[COLOR=DarkRed]yum install nautilus-actions[/COLOR]            via fedora

Here is a link to nautilus-actions website tutorials. ENJOY! ;-)
[http://www.grumz.net/?q=taxonomy/term/10/9&PHPSESSID=68a818f0046eed50167e4d8147c0e42c](http://www.grumz.net/?q=taxonomy/term/10/9&PHPSESSID=68a818f0046eed50167e4d8147c0e42c)

NOTE------> Is it just me or what? But could we get the spelling right for the title of the thread so search engines can find this link more effectively.
Nautilus not Natilus

---

### Post by satish_j on 2011-11-28
What if update happens???Most of the updates involves changes to nautilus,in which case the said procedure has to be repeated again..
or the user has to exclude the nautilus update packages during system/kernel upgrades..

---

