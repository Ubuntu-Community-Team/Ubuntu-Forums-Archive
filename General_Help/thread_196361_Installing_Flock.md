---
title: "Installing Flock"
date: 2006-06-14
forum: General Help
---

### Post by Noah0504 on 2006-06-14
Flock released beta 1 of their web browser today.  I've tried it out, but now I'd like to make it a little more "permanent."  I've currently been running Flock from my home directory, but it's not exactly the best place for it; however, I'm not sure where I should move the Flock directory: /bin, /opt, etc...

Anyone, once I figure out where to move it to, is that all I need to do?

---

### Post by blackjack6.21.91 on 2006-06-14
There really aren't many restrictions on this type of thing like there are in Windows.  Two places where applications are often put are /opt and /usr/bin, but anywhere is fine, theres nothing wrong with it being in the home folder!

I would recommend, though, if you decide to keep it in your home folder, that you change the folder name to .flock, for organizational purposes.

---

### Post by Noah0504 on 2006-06-14
Thanks.  I'm still learning how things are sorted on Linux.  I've decided to just keep it in my home folder.  (I forgot about being able to hide it by naming it ".flock".)

---

### Post by dolson on 2006-06-14
You can also hide items from your desktop by doing something like `echo flock >> .hidden` This works in GNOME, not sure if it'll work in KDE. You can simply edit the .hidden file later on to delete the names of files/directories that you want to unhide again.

---

### Post by gamma on 2006-06-15
[QUOTE=dolson]You can also hide items from your desktop by doing something like `echo flock >> .hidden` This works in GNOME, not sure if it'll work in KDE. You can simply edit the .hidden file later on to delete the names of files/directories that you want to unhide again.[/QUOTE]
Wow! Thank you. I didn't know there was a way to hide files in nautilus. I've got a few conf files that are created without the . in front so it gets annoying to see them all the time.

What I do for my custom software is I made a ~/Applications folder that has seperate directories for all my software (last.fm, mupen64, twonkymedia, etc). Then I made a ~/.bin directory that contains files pointing to the binary in the Applications folder. These files contain code such as ```
#!/bin/bash
cd ~/Applications/Last.fm-1.1.4
./player
```Changing to the directory the binary in ususally prevents problems from happening. Don't forget to chmod +x filename to make it executable :P.

To use .bin you're going to have to either edit ~/.bashrc or add the line ```
export PATH="~/.bin:$PATH"
```

Enjoy.

---

