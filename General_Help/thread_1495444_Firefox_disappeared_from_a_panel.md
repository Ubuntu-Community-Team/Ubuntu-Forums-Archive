---
title: "Firefox disappeared from a panel"
date: 2010-05-28
forum: General Help
---

### Post by Amused2Death on 2010-05-28
Ok, take it as read im still learning Ubuntu :) and occassionally do stupid things, like click on the unsubcribe buttons on unwanted email.

Did that and for some obscure reason i lost the default firefox icon from the top task bar. I could make a launcher on the desktop but i failed to find the firefox exe. I did get it to show hidden files, found the firefox folder but no exe file or similiar to launch.

Would someone be so kind as to tell me where to drill so i can at least put the firefox launcher on the desktop. As a fill in im using chromium, and i did find its folder hidden in firefox's.

ie... [username]/mozilla/firefox/chromium ??

thanks in advance

---

### Post by allquixotic on 2010-05-28
The firefox binary is /usr/bin/firefox

Most applications installed at the system level (i.e., not as a regular user) reside somewhere in /usr, with the executable binary being in /usr/bin.

There's no file extension for executable programs on Linux, so you'll just have to remember that they are in /usr/bin. :)

Also check Applications -> Internet -> Firefox to see if a Firefox icon is there.

If your FIrefox icons are really, totally gone, reinstalling Firefox should help. Use the Ubuntu Software Center for that.

---

### Post by Amused2Death on 2010-05-28
Sweet, and thanks again.
Will eventually get there :)

---

### Post by Soul-Sing on 2010-05-28
```
firefox %u
``` in the terminal does start firefox?
there are known problems with panels on 10.4
you were talking bout an .exe file is that correct?
> i failed to find the firefox exe.

---

### Post by cryptotheslow on 2010-05-28
Does Firefox still exist in the Applications menu?

Applications > Internet  you should see it in the list there.

If it is then simply right-click on it and click on the "Add this launcher to panel" option.

---

