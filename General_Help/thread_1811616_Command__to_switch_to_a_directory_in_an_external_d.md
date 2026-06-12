---
title: "Command  to switch to a directory in an external drive"
date: 2011-07-25
forum: General Help
---

### Post by p3aul on 2011-07-25
For some reason I cant get the syntax to switch to a directory in my external harddrive. I know I've done it before but now I can't get it to work. Here is what I've done.

cd /home/media/My Book/folder Where MyBook is the name of the hard drive.

Thanks,
Paul

---

### Post by CharlesA on 2011-07-25
```
cd /home/media/My\ Book/folder
```

Have to escape spaces or wrap quotes around the whole path.

If that doesn't work and you are sure the drive is mounted post the output of this command:

```
mount
```

---

### Post by ~!geek!~ on 2011-07-25
The extent I know about Linux: the default mount point for all external devices are there in /media directory. 

So if I were using a device named X, I would go to the directory /media/X/ with escape sequences for space as required.

---

### Post by p3aul on 2011-07-25
I found a script that will let me open a command prompt in any directory. That's all I wanted anyway!
Thanks,
Paul

---

### Post by CharlesA on 2011-07-25
> **p3aul said:**
> I found a script that will let me open a command prompt in any directory. That's all I wanted anyway!
Thanks,
Paul
Which script?

---

### Post by p3aul on 2011-07-26
I was a little intimidated at first because at first glance it looks complicated, but I just followed the steps and ...Success!! Here's the link  an it works beautifully!

[http://www.cyberciti.biz/faq/linux-gnome-open-terminal-shell-prompt-here/](http://www.cyberciti.biz/faq/linux-gnome-open-terminal-shell-prompt-here/)

BTW I think my problem was with the two word name for my external drive. with My internal drive(Acer) the cd command worked fine. 

Paul

---

### Post by oldos2er on 2011-07-26
nautilus-open-terminal is in the repositories, for what it's worth.

---

