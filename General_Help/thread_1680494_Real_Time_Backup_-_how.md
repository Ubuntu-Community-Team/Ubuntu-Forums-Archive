---
title: "Real Time Backup - how?"
date: 2011-02-02
forum: General Help
---

### Post by Quarkrad on 2011-02-02
I've tried to google but not much luck.  What I would like to do is have anumber of folders on my desktop and their contents, replicated/duplicated into another folder on the same PC in real time.  So for example, if I were to change an OpenOffice document in a specific folder on my Desktop it would be replicated/duplicated in real time.  If I had three folders on my Desktop A, B and C they would also appear/be backed up (in real time) in a folder called /home/backup.  Can this be done?

---

### Post by Cheesehead on 2011-02-02
Yes.  Look at the 'dnotify' package.

---

### Post by takisan on 2011-02-02
I don't know much about real-time, but you could write a script and have it run once an hour or every half-hour. I think it's gnome-scheduler that you can set programs to run automatically. The Script'd probably be something like:
```
#/bin/bash
copy -rf /home/user/desktop /home/user/backup
```
Sorry if I couldn't be much more help.

---

### Post by Quarkrad on 2011-02-03
Example:  Copy the contents in real time of two folders A and B on your Desktop to a folder called Backup elsewhere on your PC.  In Backup create two folders A and B.  Have two nautilus windows open - one showing the contents of Backup and the other showing your Desktop.  Left click folder A in Backup whilst holding down Crtl & Shift keys and drag folder A to your Desktop.  Do the same for folder B holding down Crtl & Shift.  This will put two folders A and B on your Desktop.  What ever you do re A and B will appear in Backup.

---

