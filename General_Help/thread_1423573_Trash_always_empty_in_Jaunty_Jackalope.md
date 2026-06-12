---
title: "Trash always empty in Jaunty Jackalope"
date: 2010-03-06
forum: General Help
---

### Post by cloud3737 on 2010-03-06
Just installed 9.04 on a new machine. Files I delete just seem to disappear completely instead of going into Trash. This is not what happened on my older machine. Should I be worried?

---

### Post by flippo on 2010-03-06
Hmmm, try this:```
cd ~/Desktop
touch filenamenothingwillhave
<a file named filenamenothingwillhave will appear on the desktop, right click delete it>
sudo updatedb
<this may take a while>
locate filenamenothingwillhave
```
If the locate command comes up with it, then the file has been moved wherever locate says it has, if not then it no longer exists on your system.

---

