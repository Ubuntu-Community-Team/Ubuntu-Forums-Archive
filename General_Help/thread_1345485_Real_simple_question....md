---
title: "Real simple question..."
date: 2009-12-04
forum: General Help
---

### Post by TheOnlyMrK on 2009-12-04
In order for Skype to be able to use my webcam I have to run it in a terminal by typing "LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype". My problem is it's annoying to have to run Skype in a terminal all the time and sometimes I forget to, is their a way I can set the button in the menu for Skype to run that command when I click it and make it so a terminal isn't needed?

Forgot to add in... Here's the error I get when I simply make a new menu item with the "LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype" command;
"Failed to execute child process "LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so" (No such file or directory)"

---

### Post by Diametric on 2009-12-04
I bet a script could be used to execute this operation.  I Don't know enough of scripting other than to say I'd wager this process could be automated, like you say.

---

### Post by TheOnlyMrK on 2009-12-04
Well right now I know nothing of scripting. Hopefully some time in the near future I can get into it a bit.

---

### Post by TheOnlyMrK on 2009-12-04
> **TheOnlyMrK said:**
> Well right now I know nothing of scripting. Hopefully some time in the near future I can get into it a bit.

Though I have to say I am now proud of myself by just a random guess I got this to work... Lol. I made a blank file and named it "Skype with webcam fix" then in it I put "LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype", saved it and made it executable and pointed the Skype menu button to the file and it works perfectly.

Sorry for the semi-pointless thread I made now but hopefully this info will be useful to someone in the future.

---

### Post by Diametric on 2009-12-04
MrK, I'm writing my first script right now....really.  I got myself a "Sam's, teach yourself Linux" book...I recommend doing the same if you're really interested in becoming proficient with Linux.  I know this doesn't help your issue, but I might also post this question in the beginners section...I've found others reply a bit better with these sort of questions; and like I said, do some homework on learning the terminal.  Good luck, mate.

---

