---
title: "How do I undo: echo 'ndiswrapper' | sudo tee -a /etc/modules"
date: 2011-11-16
forum: General Help
---

### Post by TheSluiceGate on 2011-11-16
As advised by this stickied thread - [http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847) - I ran this code in the console to ensure ndiswrapper launches at every startup - but now my system doesn't launch at all. I just get a black screen with a flashing cursor at the top left...

```

echo 'ndiswrapper' | sudo tee -a /etc/modules

```

Is there a line of code to undo this?

---

### Post by spiritson on 2011-11-16
Can you get into the recovery mode through GRUB, and drop to root shell prompt?

---

### Post by TheSluiceGate on 2011-11-16
Yes I can. But I don't know what line of code to run or what file I can edit to remove the force loading of ndiswrapper at startup.

---

### Post by t0p on 2011-11-16
The command **echo 'ndiswrapper' | sudo tee -a /etc/modules** added a line containing the word "ndiswrapper" to he file /etc/modules.  So you need to delete that last line.

Boot a live disk, then navigate to the /etc directory of the computer's hard drive, open the file /etc/modules with a text editor and delete the line (probably the last line) that says "ndiswrapper".

Now restart (removing the live disk of course).  Hopefully that'll do the trick.

---

### Post by TheSluiceGate on 2011-11-16
Great, thanks! That worked...

But just to say this, I had to come up with a workaround because I could not directly edit the "modules" file with a text editor.

So I ran the live CD and opened the folder with the "modules" file in it, right-clicked the background of the window the file was in and selected "Open Terminal Here"

Then I ran ```
 sudo pico modules 
```

and edited and saved the file...

Thanks!

[SIZE="1"]now if only my wifi would work too! ;) [/SIZE]

---

