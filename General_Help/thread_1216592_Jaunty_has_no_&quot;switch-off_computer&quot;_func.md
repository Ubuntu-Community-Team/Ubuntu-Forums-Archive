---
title: "Jaunty has no &quot;switch-off computer&quot; function."
date: 2009-07-18
forum: General Help
---

### Post by Jerriy on 2009-07-18
I recently upgraded to jaunty (directly by clicking the provided upgrade button in the software-update dialogue-box. Initially I thought things went well, but now I'm encountering problems, the most significant of which is that the "shut down" option that is found in the menu of Gnome desktop panel is not working. When I press it the computer refuses to shutdown. All it does is start a one-minute countdown timer.

---

### Post by Jerriy on 2009-07-18
[img]http://ubuntuforums.org/attachment.php?attachmentid=121168&d=1247678755[/img]

---

### Post by t4thfavor on 2009-07-18
For some reason there were two menus , one does all the tasks like shut down. log off hibernate, etc, while the other only logs off, or switches user. Sorry I could not be of more help, but The menu is probably there, and if its not you can add it by right clicking the panel and seecting Add to Panel.

---

### Post by JohnnySage50307 on 2009-07-18
Is it just showing that one minute popup, counting down, then closing the popup?  If you didn't let it run the full minute or click the "shutdown" button in that popup, that could explain your dillema.  If waiting the full minute and/or clicking that button isn't working, then it sounds like you have a bug somewhere.

---

### Post by Jerriy on 2009-07-18
What happenes when I press that "Shut Down" button on the popup window is that it does the same thing that the button next to it ("Cancel") does: it just shuts down itself, i.e. the timer.

---

### Post by JohnnySage50307 on 2009-07-18
Interesting...
 
Well, I'm sorry I wasn't much help

---

### Post by Jerriy on 2009-07-18
> **t4thfavor said:**
> For some reason there were two menus , one does all the tasks like shut down. log off hibernate, etc, while the other only logs off, or switches user. Sorry I could not be of more help, but The menu is probably there, and if its not you can add it by right clicking the panel and selecting Add to Panel.That's what I don't understand. By the way that exact timer also appears when I press the hibernate, sleep etc buttons. That wasn't the case when I had intrepid. 

As for your "add to panel" suggestion that only provides a new shutdown icon (it doesn't solve the menu option "shutdown" that is already there in the logout-menu.

Let's see what happens if wipe that thing out of the panel and reinstate it (removing it but then adding it back to the panel)...

---

### Post by girimam on 2009-07-18
For a temporary solution you can always use

```
sudo shutdown -h now
```throguh a terminal 

the now can be replaced by a time or +<no of min>


-r option for reboot


your problem looks more of a gconf-editor problem running the wrong script. Could find it though

---

### Post by cariboo on 2009-07-18
You can stop the the countdown timer from coming up by right cilcking on the fast switch user icon (the little green man) and select preferences and disable the notification. BTW the counter timer is the default behavior in Jaunty.

---

