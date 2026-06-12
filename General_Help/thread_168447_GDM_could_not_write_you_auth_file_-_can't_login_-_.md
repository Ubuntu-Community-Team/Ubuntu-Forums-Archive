---
title: "GDM could not write you auth file - can't login - .help"
date: 2006-04-30
forum: General Help
---

### Post by dotdot on 2006-04-30
hi folks....

I'm trying to do something i thought simple...

My laptop is dual boot - i have 5gb allocated to ubuntu  - and the 
remainder  for now windows..
So I boot win - pick a partition i dont want - then reformat it as ext2. 
So that I can then have another fs in ubu - for linux usage.
I thought this the best approach as it was previously used by 
windows - so i thought I'd have windows sort it... for linux 
usage. (using partition magic btw).

So i reboot into ubuntu - and can't login ... AT ALL..

I get this little popup saying..
GDM could not write to your authorization file.... Please contact your administrator....

Which then cycles you back to the login screen... no joy...

have had a read of prev [thread]("http://ubuntuforums.org/showthread.php?t=137174&highlight=gdm+authorisation") - however this one doesn't advise how to get in if you have this problem.

..I'd rather not re-install to fix this problem - any pointers would 
be much apprec.

..

---

### Post by trent dillman on 2006-04-30
Delete the following:

~/.ICEauthority
/tmp/gconf-(your user)

see if that helps.

---

### Post by dotdot on 2006-04-30
ok triedd that - moved the file out of the way - no joy.

the second part - there is nothing in /tmp

.. any other ideas..... 

oh and btw - i've booted into safe mode... root command prompt.
loks useful... oh and my keymap is ideal in root in safe mode - but never was in normal mode.... (another [thread..)]("http://ubuntuforums.org/showthread.php?t=161267")

..problems problems... we don't mind ... its the only way we learn - anything.

---

### Post by dotdot on 2006-04-30
ahem - he said cap in hand...

i've just booted up safe mode.. and thought "eh hang on - give me a df !" 
... oops.

/ was full - ie hence the need for the new filesystem.
Removed offending file .. then rebooted eh voila.
Login now possible...


 ... UE - or user error - if you're diplomatic.

..thanks all the same.

now back to my [keyboard]("http://ubuntuforums.org/showthread.php?t=161267") story...

---

