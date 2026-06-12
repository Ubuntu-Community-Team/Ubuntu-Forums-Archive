---
title: "Truecrypt on Xubuntu"
date: 2011-10-28
forum: General Help
---

### Post by cottfcfan on 2011-10-28
Is anyone using truecrypt successfully on Xubuntu without having to install Nautilus?
It installs & mounts ok, but everytime I try and open the volume I get the message, "No such file or directory:nautilus"
Any help would be much appreciated.

---

### Post by alenis on 2011-10-28
The volume should be mounted in the directory /media/tryuecrypt1. Simply navigate to it with Thunar.
However, you can use this trick to "replace" nautilus with thunar: create a file called nautilus in /usr/bin with the following content:

#!/bin/bash
exec thunar $3
exit 0

Don't forget to make it executable!

---

### Post by cottfcfan on 2011-10-28
Thanks alenis.
The 2nd idea worked perfectly.

---

### Post by coltlacrosse on 2013-03-10
Could someone please provide a quick tutorial on how to create the file mentioned in post #2 and how to make it executable? All I really know how to do in terminal is cd around the file system.

---

### Post by Stonecold1995 on 2013-03-10
> **coltlacrosse said:**
> Could someone please provide a quick tutorial on how to create the file mentioned in post #2 and how to make it executable? All I really know how to do in terminal is cd around the file system.
I actually think the way he suggested is a little inefficient.  It would be a better idea to run this command:
```
sudo ln -s /usr/bin/thunar /usr/bin/nautilus
```

It'll ask you for your user password, enter it and it will create a file called "/usr/bin/nautilus" that links to "/usr/bin/thunar".

In case you still want to use the other method for whatever reason, then here's how:
1: Open terminal
2: Run "sudo gedit /usr/bin/nautilus" (replace gedit with whatever text editor Xubuntu uses)
3: Copy+paste
```
[COLOR=#000000]#!/bin/bash[/COLOR]
[COLOR=#000000]exec thunar $3[/COLOR]
[COLOR=#000000]exit 0
```
into it and save
4: Run "sudo chmod +x /usr/bin/nautilus" (this is the command which makes something executable)

Also, it would probably be a better idea to create a new thread asking how do do this, rather than resurect one from 2011.[/COLOR]

---

### Post by overdrank on 2013-03-10
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

