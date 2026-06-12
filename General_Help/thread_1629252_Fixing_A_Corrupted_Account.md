---
title: "Fixing A Corrupted Account"
date: 2010-11-23
forum: General Help
---

### Post by cwklinuxguy on 2010-11-23
Hey guys :(

My account has gotten corrupted by...me earlier today and it is very annoying. I turned on Docky, then decided that I wanted a new panel (forget what for) so I rightclicked and did "New Panel" then I selected "Left" (to put it on the left side) the computer froze. I had no option but to force the computer to shut down [or did I???] So I did that. When I rebooted, I tried to log into my account. Once I enter my password it just sits there on the "Ubuntu" screen. So, I forced shutdown a second time and ran recovery mode. No effect. Repeated process two more times. No effect. Forced shutdown yet again and booted into Windows, works fine. Shut that down and logged into a user account that I have but don't really use. Works fine. I've managed to migrate some of my data over to the new user account, but some of it (web history, saved ff passwords, GTG Tasks,. etc) I don't know how to get over and I need some of that stuff. I use the computer for school, mostly...so I'm not gonna die if it's not fixed immediately, but I would appreciate any help with making my account work the way it should.

P.S. I have logged in successfully to the corrupt account, but the notification area is gone, the menus are unusable, and the whole thing is primarily useless.

---

### Post by WorMzy on 2010-11-23
Boot up the Ubuntu installation but don't log in. Press Ctrl+Alt+F1 instead, and log into the tty that this brings up. Do you get any error messages? Post them here if you do.

If not, you can reset your panels to their default state with the following commands:
```
mv ~/.gconf/apps/panel ~/panel
gconftool-2 --shutdown
```

After running these two commands, switch back to the graphical logon screen with Alt+F7 (If that doesn't give you the graphical logon screen, press Ctrl+Alt+F8 ) and log in.

Has that fixed things? Made them worse?

If they're worse, switch back to the tty (Ctrl+Alt+F1) and run

```
sudo service gdm stop
rm -r ~/.gconf/apps/panel
cp -r ~/panel ~/.gconf/apps/
```

That should put things back to how they were, and we've eliminated the panels as the source of the problem. The only other application you mentioned is Docky. Unfortunately, I've never used it, so I have no idea where it puts it's config files. If you can find them (use ls to check in ~/.gconf/apps, ~/.config, ~/.local and possibly even ~/.docky), mv them to a different location and see if that helps.

You can start gdm (the graphical interface) up again with
```
sudo service gdm start
```

---

### Post by cwklinuxguy on 2010-11-23
Upon entering the first line of code, I receive [quote=Ubuntu Command Line] mv: invalid option -- ' /'
Try 'mv --help' for more information [/quote]

---

### Post by cwklinuxguy on 2010-11-23
I did it again, realizing that they are '~' and not '-'. I receive: >  mv: target '/home/chris/panel' is not a directory 

---

### Post by WorMzy on 2010-11-23
Take care to input the commands exactly as I've written them. You shouldn't get that error if you've type it in right. Double check before executing. :)

---

### Post by cwklinuxguy on 2010-11-23
Works like a charm. Much appreciated. Thanks.

---

### Post by WorMzy on 2010-11-23
Glad to hear it. Don't forget to [mark your thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") using the thread tools at the top.

---

