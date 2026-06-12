---
title: "What does a padlock by a file mean?"
date: 2011-04-13
forum: General Help
---

### Post by jacatone on 2011-04-13
I'm running Ubuntu 10.10. I notice a lot of files have a little padlock in the upper right corner and they don't appear in an ls command. What does that mean? Thanks.

---

### Post by Rasa1111 on 2011-04-13
It means they are "locked" and you are not able to change/remove/edit them. 
Meaning, you do not have permissions to do so.

---

### Post by WorMzy on 2011-04-13
Use ```
ls -l
``` to see more information about files. A padlock means that you do not have write permissions on the file. A no entry sign means that you do not have read permissions.

---

### Post by Rubi1200 on 2011-04-13
In addition to what has been said above, be very wary of changing permissions or even trying to edit essential system files. Not only can it reduce security, you could also end up with an unstable and unbootable system. 

If there is a specific file that you need to access/edit etc., better to ask here first.

---

### Post by jacatone on 2011-04-14
I'd like to put a copy of the "Computer" icon which is in the applications folder onto my desktop. How would I do that without the big padlock showing?

---

### Post by WorMzy on 2011-04-14
How are you copying it? If done through the GUI, the copy should be created with read+write+execute permissions for your user (assuming you're using the default umask of 022). If you're copying via terminal then you should still have read and write permissions, but not execute permissions (for some reason).

Unless you're using gksu or sudo when copying it, I can't see any reason why you would get a padlock icon.

Can you run

```
ls -l /path/to/the/copy
``` (replacing "/path/to..." with the actual path) and paste the output here.

---

### Post by yetiman64 on 2011-04-14
> **jacatone said:**
> I'd like to put a **copy of the "Computer" icon which is in the applications folder onto my desktop**. How would I do that without the big padlock showing?

In terminal use,
```
gconf-editor
```Go to (expand the tree) Apps > Nautilus > Desktop and in the top right hand window pane tick the entry "computer_icon_visible". An icon for the place "Computer" should now be on the desktop.

---

### Post by Rasa1111 on 2011-04-14
> **yetiman64 said:**
> In terminal use,
```
gconf-editor
```Go to (expand the tree) Apps > Nautilus > Desktop and in the top right hand window pane tick the entry "computer_icon_visible". An icon for the place "Computer" should now be on the desktop.

Yeo, What yetiman said.
 In addition, You can also use Ubuntu tweak to do it, if you have it installed. 
 
Like so~
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=189085&stc=1&d=1302830500[/IMG]

---

