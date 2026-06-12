---
title: "Theme doesn't always load on login"
date: 2010-03-05
forum: General Help
---

### Post by ld.4lpha on 2010-03-05
When I log in locally, sometimes my theme isn't applied.  This problem started a few weeks ago, but before that the same theme would load just fine every time.

In order to get my chosen theme to load, I go System > Preferences > Appearance.  As soon as I click "Appearance"...boom.  My theme loads and all is fine.  I don't have to change settings or anything....just start the "Appearance" utility.

This doesn't all of the time, only sporadically.  

Another thing to mention is that I'm using AWN.  When this happens, AWN doesn't load all of the launchers.  I killall and restart AWN and all is good there.

Anybody have a clue what could be going on?  Compiz related?

---

### Post by pvtjsauk on 2010-03-14
I have this same problem.  I completely reset all appearance settings back to default and it still didn't fix it.  (it worked for 2 days and then did it again).  Its not AWN because i'm not running that and its happening to me.  Its really starting to piss me off though and i cannot figure it out for the life of me.  If anyone knows the answer to this problem i would really appreciate it.

---

### Post by slipdipper on 2010-03-23
same issue here..

---

### Post by spyder0080 on 2010-03-24
Same here. I'm also using compiz and emerald (but not awn). I'm not sure if they cause this problem; does anyone have this problem without compiz and emerald?

EDIT: I also notice sometimes when I open folders (such as music), the theme in that window is different from the rest. I've uploaded a screenshot

---

### Post by jamesoy on 2010-07-26
same here. anyone has a fix yet?

thanks!

---

### Post by Clutchface on 2011-03-14
> **ld.4lpha said:**
> When I log in locally, sometimes my theme isn't applied.  This problem started a few weeks ago, but before that the same theme would load just fine every time.

In order to get my chosen theme to load, I go System > Preferences > Appearance.  As soon as I click "Appearance"...boom.  My theme loads and all is fine.  I don't have to change settings or anything....just start the "Appearance" utility.

This doesn't all of the time, only sporadically.  

Another thing to mention is that I'm using AWN.  When this happens, AWN doesn't load all of the launchers.  I killall and restart AWN and all is good there.

Anybody have a clue what could be going on?  Compiz related?

I am having the exact same issue... any solutions?

---

### Post by highspider on 2011-03-14
I know this will not fix it SORRY IDK
 
* Get to the System->Preferences->Keyboard menu.
 * Select the “Layouts” tab and click on the “Layout Options” button.
 * Then select “Key sequence to kill the X server” and enable “Control + Alt + Backspace”.
   enable as in check the the box

But will let you use CTRL+ALT+BACKSPACE to restart X11 hopeful your theme will pop up fast till someone can solve it.

---

### Post by horace on 2011-03-14
> **spyder0080 said:**
> Same here. I'm also using compiz and emerald (but not awn). I'm not sure if they cause this problem; does anyone have this problem without compiz and emerald?


Yes, this happens to me occasionally even though I have visual effects set to "none". It doesn't happen often enough for me to be able to see a pattern of events though.

---

### Post by kailkitsune on 2011-03-14
i had the same problem for about a day. emerald, compiz, and the normal appearance thingy(completely forgot the name...)where clashing i used "compiz fusion icon"(its in the software center) to fix the clash. after that all i had to do was add cfi to start up.

i don't know if this will help you guys but its better than nothing i hope.
good luck:D

---

### Post by highspider on 2011-03-14
I have had compiz issue before that effect the desktop behaviour. 

you could TRY reinstall compiz. :?:
  This won't erase your settings and custom what nots.
   ..ergo you wont have reconfigure all your custom compiz settings 

this code will show what compiz things you have currently installed 
```
 
dpkg --get-selections | grep compiz

```this code will reinstall compiz things from above code -fit to your needs-
```

sudo apt-get install --reinstall compiz compiz-core compizconfig-settings-manager 
sudo apt-get install --reinstall compiz-gnome compiz-plugins compiz-fusion-plugins-main
sudo apt-get install --reinstall compizconfig-backend-gconf

```I broke giant command into three commands for readability

---

### Post by faflu on 2011-03-15
> **spyder0080 said:**
> does anyone have this problem without compiz and emerald?


I have compiz switched off and have the same issue. It's account-related, as other accounts on my computer are not affected by this annoyance. The difference with your cases is that it happens to me **every** time I restart the computer.

---

