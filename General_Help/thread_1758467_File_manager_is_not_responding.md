---
title: "File manager is not responding"
date: 2011-05-14
forum: General Help
---

### Post by Artemis Fowl on 2011-05-14
Hello,
I have upgraded to 11.04 today. I am somewhat dissapointed for various reasons, but my worst problem is the fact that file manager (nautilus, I think?) no longer works. When I try to open a folder, it will display "Opening [folder]..." on the taskbar, but it shortly dissapears and nothing happens. When I log out, something informs me that File Manager is not responding.
What should I do here?

---

### Post by sennett on 2011-05-14
Few things I would try:

[LIST=1]
[*]Different file manager (Thunar).
[*]Select Ubuntu Classic at the bottom when you log in.
[*]Try moving all the hidden folders related named .gconf, .gconfd, .gnome2, .gnome2_private (I moved them all to a backup directory ~/tmpgnome when I updated to 11.04 and it solved a few things).  If you try this make sure you are comfortable moving around the system using the command line.  If Gnome breaks that is all you'll have to restore those dirs.
[/LIST]

---

### Post by TeoBigusGeekus on 2011-05-14
Open a terminal and give
```
nautilus
```
Post us any error messages you get.

---

### Post by Artemis Fowl on 2011-05-14
> **TeoBigusGeekus said:**
> Open a terminal and give
```
nautilus
```Post us any error messages you get.

```
(nautilus:12273): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```

Edit: Weird, it seems to have fixed itself.

---

### Post by Artemis Fowl on 2011-05-15
Well, it did fix itself, but now it's back. Same Unique-Dbus-WARNING. Interestingly, gksu nautilus still works.

---

### Post by TeoBigusGeekus on 2011-05-15
Then it must be something with your user preferences from Maverick.
Try deleting the ~/.gnome2 and ./gconf folders and see if that helps.

---

### Post by Artemis Fowl on 2011-05-15
> **TeoBigusGeekus said:**
> Then it must be something with your user preferences from Maverick.
Try deleting the ~/.gnome2 and ./gconf folders and see if that helps.

Well, now it's randomly working again. Is moving the folders to trash sufficient?

---

### Post by Artemis Fowl on 2011-05-16
And It's not working whatsoever now. Help, please, anybody?

---

### Post by kunkas on 2011-07-14
I have the same problem :(

---

