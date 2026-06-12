---
title: "Dropbox app difficulties"
date: 2010-02-02
forum: General Help
---

### Post by scrambledarthur on 2010-02-02
Hello all!

I recently ran into what appears to be a rather groovy software by the name of dropbox. I can work it online well enough, but in order to get full use of it, it should be able to work from outside of a web browser.

I downloaded the program, but when I clicked on the app, it said that I needed to download the proprietary daemon. It wasn't able to properly connect to the server, and so I manually downloaded and extracted it to my home folder. The file is hidden, and so when I used terminal to bring it up, I saw the little dropbox icon at the top of my screen, but when I click on it, an error message pops up, claiming it cannot be found and suggesting that I misspelled the command despite my copy-and-pasting it.

When I look at the terminal after clicking on the icon, it reads: "(nautilus:3197): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed"

I have many projects in mind for this software, and I really want to stay ubuntu, so any help or solutions would be greatly appreciated.

---

### Post by jamesisin on 2010-02-02
Use these instructions for installing dropbox:

[http://www.ubuntugeek.com/howto-install-dropbox-in-ubuntu-9-10karmic9-04jaunty8-10intrepid8-04hardy.html](http://www.ubuntugeek.com/howto-install-dropbox-in-ubuntu-9-10karmic9-04jaunty8-10intrepid8-04hardy.html)

It uses repositories and will make you much happier in the end.

---

### Post by scrambledarthur on 2010-02-03
Thanks a bunch. I'm working on it and it's looking promising so far. I'll update this to [solved] should it work!

---

### Post by scrambledarthur on 2010-02-03
Hmm it appears to be having the exact same problem...I see the little dropbox icon (so close, yet so far!), but when I click on it, all it says is that it couldn't find the directory, and rather cheekily suggested that my spelling may be at fault.

It appears as though many programs within ubuntu get touchy when the /home folder is concerned. I don't know how. I botched the installation once, but reformatted my drive and gave it another go.


hmmmm

---

### Post by jamesisin on 2010-02-03
Is /home on / or did you put it on a separate drive?

What path are you using for the dropbox folder?

---

