---
title: "created accident folder link thing, how to remove?"
date: 2009-08-17
forum: General Help
---

### Post by paks.dreamer on 2009-08-17
Guys, I stuffed up a command, and I have an unwanted weird thingy I need to remove. :s  I guess it was bound to happen as a relatively new user, and being frustrated with these commands I was using not working as intended, I got a bit quick in my typing.

In running the command:
**ln -s /usr/local/rar2.71/rar .**

I accidentally ran:
**ln -s /usr/local/rar2.71 rar .** <-- with a space instead of /

Here is the outcome.. this folder link type thing seemingly named rar. (it's the one on the left):
**[http://img.photobucket.com/albums/v300/Koyukionna/Screenshot-3.png](http://img.photobucket.com/albums/v300/Koyukionna/Screenshot-3.png)**

I've tried various "sudo rm" combinations trying to get rid of that thing, but can't work out what it's really called, or how to actually remove it.  Do I have to go into something and reedit a line somewhere instead?

Sorry for my silliness, and any help would be greatly appreciated.
[SIZE=1][I]
~Paks.[/I][/SIZE]

---

### Post by scouser73 on 2009-08-17
Enter this command: **gksudo nautilus** into Terminal, locate the file, right click and delete.

---

### Post by paks.dreamer on 2009-08-17
Wow, straight to "root" -- scary!

Thanks so much scouser73, I'm glad it was this simple. :]

---

