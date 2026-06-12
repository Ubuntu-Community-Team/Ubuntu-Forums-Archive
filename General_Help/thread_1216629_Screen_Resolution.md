---
title: "Screen Resolution"
date: 2009-07-18
forum: General Help
---

### Post by oldtraveler on 2009-07-18
[color=red]SOLVED.(See #7 below)
[/color] Using Ubuntu 9.04 and trying to do as this thread below instructs I can not locate "Configuration Editor from the System Tools menu" nor can I find "/desktop/gnome/screen/default/0/".

Or is there an easier way to set the screen resolution to stay each time I open Ubuntu?
-------------------------------------------------------------
" Re: Why must I set the correct screen resolution on every startup?
do the following:

Click the applications menu, select Configuration Editor from the System Tools menu.

Now go to the following key (location):

/desktop/gnome/screen/default/0/

In the right pane you should see a key called 'resolution', double click this and enter your preferred resolution in the value box.

restart

You should find that everytime u login your preferred resolution is in use."

---

### Post by CatKiller on 2009-07-18
> **oldtraveler said:**
> I can not locate "Configuration Editor from the System Tools menu"

Press Alt-F2 and type **gconf-editor** in the box.

---

### Post by ajgreeny on 2009-07-18
Just to make life easier in future, you can right click on the menus and choose to "Edit menu" where you can put a check mark in the Configuration Editor box, and while you're at it, any other applications you might prefer to show in the menus that don't at the moment.

@ oldtraveler.
> Now go to the following key (location):

/desktop/gnome/screen/default/0/Where did this key come from?  I was surprised to see your comment so just had a look, and it doesn't exist, not in jaunty, at any rate.

---

### Post by oldtraveler on 2009-07-18
> **CatKiller said:**
> Press Alt-F2 and type **gconf-editor** in the box.
That works, but I'm not sure where to go from here.

---

### Post by oldtraveler on 2009-07-18
> **ajgreeny said:**
> Just to make life easier in future, you can right click on the menus and choose to "Edit menu" where you can put a check mark in the Configuration Editor box, and while you're at it, any other applications you might prefer to show in the menus that don't at the moment.

@ oldtraveler.
Where did this key come from?  I was surprised to see your comment so just had a look, and it doesn't exist, not in jaunty, at any rate.

1. I don't know what "menu" you suggest right clicking on.

2. I agree that "/desktop/gnome/screen/default/0/ " doesn't seem to be there.

---

### Post by oldtraveler on 2009-07-18
> 
Quote:
Originally Posted by gilch View Post
Finally, someone posted a solution to my problem.
That was to add 'xrandr -s 1280x800' (for me it was 1920x1080) to the startup list.
This works. I hope it works for you as well.
Gilles > 
I'm working on the same problem. When I try to add xrandr -s 1024x768 I am required to enter a command. What is that supposed to be? What command?
oldtraveler
More on this problem from another older thread with the second quote being my question.

---

### Post by oldtraveler on 2009-07-18
[SIZE="4"][color=red]SOLVED[/SIZE][/color] by using xrandr -s 1024x768 as the command in System; Preferences; Display; Add.  Re-booted and lo and behold it stayed at 1024x768.

Thanks to all who replied.

---

