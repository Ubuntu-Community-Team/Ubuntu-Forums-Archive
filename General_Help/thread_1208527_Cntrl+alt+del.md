---
title: "Cntrl+alt+del"
date: 2009-07-09
forum: General Help
---

### Post by becoolpal on 2009-07-09
Is there any thing similar to Cntrl+alt+del(as in windows) in ubuntu when various applications doesn't respond or computer halts?

---

### Post by poosietgp on 2009-07-09
Hi! I think the solution youare looking for is foud here...

[http://ubuntuforums.org/archive/index.php/t-190990.htm]("http://ubuntuforums.org/archive/index.php/t-190990.htm")

---

### Post by raymondh on 2009-07-09
Hello Becoolpal,

We used to have ctrl+alt+backspace to restart X (sort of like the RE-DO combo key) .... but, if you are using Jaunty, that option has been disabled by default.  See the release notes and its' fix.

[http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904)

---

### Post by Simian Man on 2009-07-09
I usually use Crtl+Alt+F2 to get a new virtual terminal and then use killall or kill to close the offending application.

---

### Post by issih on 2009-07-09
Edit...see this is what happens when you start writing a post then get distracted...other people jump in and make you look stupid :)

The suggestions in that thread to bind the opening of gnome system monitor to ctrl-alt-delete (or indeed the shortcut of your choice) will give you an experience pretty close to window's task manager.

Be aware though that the shortcut to restart the X windowing system (ctrl-alt-backspace) has been disabled by default in jaunty, so if X has locked up to the point when you can't launch the system monitor from the menus (pretty rare to be honest) then you are stuck anyway, and it is unlikely that the shortcut would do anything in that scenario. Consequently you are literally just producing a simple shortcut to launch the application, nothing more nothing less.

You can, of course, always manage misbehaving processes using the terminal (pidof, ps and kill being particularly useful commands to learn about here), and you can always get to a terminal even if X has really broken itself.

Nonetheless, for a nice gui oriented approach the system monitor will do nicely.

Hope that helps.

---

### Post by asmoore82 on 2009-07-09
I have set keyboard shortcuts for
ctrl+alt+delete to run the System Monitor; and
ctrl+alt+escape to run `xkill`

---

### Post by poosietgp on 2009-07-09
or youcan do this...

go to System > Preferences > Keyboard Shortcuts

Once there a window will open with all the shotcut key mappings listed,
at the lower right you will see +Add button click on it and a new window will open, in the Name Textbox type ```
Run System Monitor
```, in the Command textbox type ```
gnome-system-monitor
``` then click apply. It will say something like "ctrl alt delete has been mapped to suspend action, are you sure you want to commit changes?" well it says something like that, anyways ignore that and make the changes. Now that we have made the change the new key mappings should be on the list.

now if you press Ctrl+Alt+Del the System Monitor will show, if you go the Process tab you can see the processes you want to end.

Hope this helps.

---

### Post by becoolpal on 2009-07-09
thanx a lot guys!!!

---

### Post by tea for one on 2009-07-09
> **becoolpal said:**
> Is there any thing similar to Cntrl+alt+del(as in windows) in ubuntu when various applications doesn't respond or computer halts?

When an application does not respond, you can use "Force Quit"

Right click upper or lower panel in Gnome
Select "Add to Panel"
Scroll down and select "Force Quit"
Click "Add" to install this little utility on the panel

It is perfect to kill misbehaving applications

Kind regards

---

