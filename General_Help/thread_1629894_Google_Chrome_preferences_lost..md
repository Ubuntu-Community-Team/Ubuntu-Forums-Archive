---
title: "Google Chrome preferences lost."
date: 2010-11-24
forum: General Help
---

### Post by Jetso on 2010-11-24
I have been using Ubuntu for about 2 months. I have always used Chrome and never had a problem with it. Today when I got on, a popup box showed up and said "You preference file could not be read." And a bunch of things changed. When set them how they were, and reboot, everything is screwy again. I would remove Chrome and the install it again, but I don't want to lose my Bookmarks. If I re-install will I lose them? If I will is there a way to get it to work again?

---

### Post by lovinglinux on 2010-11-24
Most likely that your issue is in ~/.config/google-chrome/Default/Preferences. So I would start deleting it to see if the problem persists. Close Chrome before doing that.

If deleting the Preferences file doesn't work, then make a backup of what you need in that folder and delete the folder ~/.config/google-chrome/, then restart.

To backup your bookmarks, open the file manager, go to ~/.config/google-chrome/Default and backup the file "Bookmarks". 

BTW, if you re-install Chrome you won't lose your settings, which means it probably won't fix your problem.

---

### Post by Jetso on 2010-11-24
It's working. Here is what I did. I went in and made copies of /home/jetso/.config/google-chrome  and it's Bookmarks and prefrences, then deleted /home/jetso/.config/google-chrome. It put a new Bookmarks file in there, so I Put the contents of my copied Bookmarks into it. Then to make sure I had a backup, I made a HTML file just in case.

---

