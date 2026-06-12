---
title: "Panels Stuck on Each Other; Can't Get Properties"
date: 2011-03-23
forum: General Help
---

### Post by Tricause on 2011-03-23
Hello all,

I am sorry if this question has been asked, but I searched and found none that described exactly what was happening to me.

I had both the taskbar panel (that starts default at bottom) and main panel (that default starts on top) both moved to the bottom because I'm used to Windows. I changed one panel to autohide, the topmost I believe, and now the two panels seem to have merged, with me being unable to right click either panel and access the panels to remedy the situation. The panels flicker erratically when I have my mouse on top of the panel and the only thing I can access is trash, power, and mail, with no other options.

I read in other posts that I should try to access the terminal, but I never set up a keyboard shortcut to the terminal and am unsure if I can access it any other way. I saw the virtual terminal, but was unable to open anything through it.

I took a screenshot to show what I have:

[http://i170.photobucket.com/albums/u264/Tricause/Screenshot.png](http://i170.photobucket.com/albums/u264/Tricause/Screenshot.png)

Please note that right clicking the panel does absolutely nothing, so I am pretty desperate at this point. I had to access the internet through my other computer to post this.

Thanks in advance!

---

### Post by Frogs Hair on 2011-03-23
Try Alt +F2 and type gnome-terminal into the box and select run . in the terminal run this command.```
gconftool --recursive-unset /apps/panel && killall gnome-panel 
```

---

### Post by Tricause on 2011-03-23
The Alt + F2 didn't work; however, I remembered that when I ran SPE Editor I could run my Python programs in terminal so I went there and started a new terminal session then ran your code and then everything reset -- so thank you very much!!!

---

### Post by Frogs Hair on 2011-03-24
Glad it worked .:D

---

