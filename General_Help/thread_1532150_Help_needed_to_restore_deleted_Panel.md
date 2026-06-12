---
title: "Help needed to restore deleted Panel"
date: 2010-07-16
forum: General Help
---

### Post by hundred1906 on 2010-07-16
I deleted my system panel (the strip at the top of the window) by mistake. In fact I thought I was deleting a sub-panel.

How do I restore or rebuild the panel because without it there is virtually nothing you can get at except through a command shell.

---

### Post by TechBeastie on 2010-07-16
I've run into this problem myself before, but I usually have at least one leftover panel floating around somewhere that I use to rebuild the one I deleted.  If that's not true in your case, you might try pressing <Alt-F2>, and entering "gnome-panel" into the run dialog that appears.  I honestly have no idea whether this will work, but it's worth a shot.

---

### Post by Vishnu V on 2010-07-16
I don't know how to  restore a lost panel, but u can create a new panel by right click on the  lower panel. Now you can add the following to the panel to get the default panel
menu bar
firefox
notification area
indicator applet
clock

---

### Post by Yarui on 2010-07-16
This is a pretty common problem.  It happened to me several times before I figured out how to properly restore it.  All you need to do is right click your bottom panel and choose "_N_ew Panel".  Move the panel to the top, right click it and choose "_A_dd to Panel..."  All of the things that are on the panel by default can be found in this list.  The only names I can remember off the top of my head is "indicator applet" and "Menu Bar".

Sorry, I'm not on my Ubuntu machine at the moment or I would check the names of the others for you.

Edit:  Looks like the post above me has made a good list.

---

### Post by TechBeastie on 2010-07-16
Better yet: I bet anything (a) there's a config file somewhere in the .gnome directory in your user profile that spells out what (if anything is in the panel), and (b) that there's some default version of this file that's automatically placed in all user accounts.  Thus, if worst comes to worst, you might try creating a new user account via the command line (useradd, I believe the command is, and then use passwd to set a login password), and then copying the pertinent configuration file from that account's home directory into your own.  Nutty idea, I know, but it might work.

---

### Post by hundred1906 on 2010-07-16
Thanks everyone. I have a top panel back now by right clicking on the lower panel as Vishnu advised. Also have some basic buttons back into place.

What is missing right now are Places, Applications and System.

---

### Post by slooksterpsv on 2010-07-16
There should be something built-in where an average user can't delete the bar at the top, but can move it and what not. I know how to get the panel back, but others may not, I wouldn't mind a prompt, items are locked on the panel, are you sure you want to delete the entire panel?

Menu Bar - Custom menu bar - is the one that should have Ubuntu button, applications, places, system

---

### Post by Humanity to others on 2010-07-16
This may help you

[http://jacobwg.com/2010/06/17/restore-original-gnome-panel-configuration-in-ubuntu-10-04/](http://jacobwg.com/2010/06/17/restore-original-gnome-panel-configuration-in-ubuntu-10-04/)

---

### Post by Yarui on 2010-07-16
> **Humanity to others said:**
> This may help you

[http://jacobwg.com/2010/06/17/restore-original-gnome-panel-configuration-in-ubuntu-10-04/](http://jacobwg.com/2010/06/17/restore-original-gnome-panel-configuration-in-ubuntu-10-04/)
Very nice method (assuming it works).  I think I will keep this one on file for next time this question comes up.

---

### Post by hundred1906 on 2010-07-16
The method posted by Humanity to Others works. It needed a bit of confidence when using because it deletes both top and bottom panels so you lose access to the Command Shell. Also the web page is shown as constantly downloading material from the jacobwg web site. In that situation just use Alt F2 to access a new command line and put into it the final command in the instructions (pkill gnome-panel) and as if by magic both panels reappear. Problem solved, thankyou.

---

### Post by jacobwg on 2010-07-31
> **hundred1906 said:**
> The method posted by Humanity to Others works. It needed a bit of confidence when using because it deletes both top and bottom panels so you lose access to the Command Shell. Also the web page is shown as constantly downloading material from the jacobwg web site. In that situation just use Alt F2 to access a new command line and put into it the final command in the instructions (pkill gnome-panel) and as if by magic both panels reappear. Problem solved, thankyou.

Hi!  I'm Jacob Gillespie (JacobWG) of jacobwg.com and I'm glad that the solution worked for you... I'm constantly messing up my panel config, so I was happy to figure it out myself... :)

I'm not sure what you mean by the site constantly downloading material from the website, but please let me know if you had any issues with the site.  I would love to fix them!  I recently changed themes in the past few days, so previous HTML issues should be resolved.

Also, are you losing access to the terminal before typing pkill gnome-panel?  If so, let me know and I'll update the page on my site.

Thanks for your comments and glad that I could be of help!

JacobWG

---

### Post by lidex on 2010-07-31
Reset panels:
```
gconftool-2 --recursive-unset  /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

---

### Post by jacobwg on 2011-01-12
Just FYI, I changed blog structure, so the new link is [http://me.jacobwg.com/145-restore-original-gnome-panel-configuration-in-ubuntu-10-04]("http://me.jacobwg.com/145-restore-original-gnome-panel-configuration-in-ubuntu-10-04")

JacobWG

---

### Post by Francewhoa on 2012-02-18
Thanks lidex. Confirming #12 works with 10.04

---

### Post by Deedon on 2012-05-18
Found this by searching and have the same problem.  I tried the step in #8 but did not get back my missing top panel, insetad I lost my bottom panel.  I don't know what to try next.

---

### Post by Deedon on 2012-05-18
> **hundred1906 said:**
>  Alt F2 to access a new command line and put into it the final command in the instructions (pkill gnome-panel) and as if by magic both panels reappear. Problem solved, thankyou.


OK, followed with just this step from post #10 and both of my panels are back.  Most of the icons I had added are missing but that I can handle.  Thanks to those that posted the helpful info.

;)

---

