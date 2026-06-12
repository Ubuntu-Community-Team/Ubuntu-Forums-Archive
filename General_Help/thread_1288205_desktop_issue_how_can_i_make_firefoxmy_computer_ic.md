---
title: "desktop issue: how can i make firefox/my computer icons to be  lock?"
date: 2009-10-11
forum: General Help
---

### Post by talphp on 2009-10-11
I got some times when i clean my desktop its deletes also the "firefox" and "my computer" icons... there is a way to set them to be unable to be delete?

---

### Post by khelben1979 on 2009-10-11
Yes, if you change to a different owner of the selected files which you want to keep, you will not be able to delete them unless you are logged in with that user.

So by using the sudo command you can do like this on a file:
```
sudo chown eric.eric test.sh
``` where eric is the owner of the file and test is the file which is going to be altered.

You'll find your desktop files by searching /home/[user]/.gnome/ (etc etc..) and you can apply this principle by using a text shell like the one found on your text terminals (ctrl + alt + f(x)) where x is the value from 1 to 6 or simply by running Gnome shell or [the xterm application]("http://en.wikipedia.org/wiki/Xterm").

Use: ```
man chown
``` if you feel uncertain about how the command works before using it.

---

