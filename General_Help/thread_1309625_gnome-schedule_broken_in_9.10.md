---
title: "gnome-schedule broken in 9.10?"
date: 2009-11-01
forum: General Help
---

### Post by Just_SomeGuy on 2009-11-01
I can't launch gnome-schedule after an upgrade to 9.10.
I tired removing/reinstalling it but I get this error:


```
gnome-schedule
/usr/share/gnome-schedule/mainWindow.py:158: DeprecationWarning: Use the new widget gtk.Tooltip
  tip = gtk.Tooltips ()
/usr/share/gnome-schedule/mainWindow.py:159: DeprecationWarning: Use the new widget gtk.Tooltip
  tip.enable ()
Traceback (most recent call last):
  File "/usr/share/gnome-schedule/gnome-schedule.py", line 74, in <module>
    mainWindow = mainWindow.main(debug_flag, False, pr, manual_poscorrect)
  File "/usr/share/gnome-schedule/mainWindow.py", line 257, in __init__
    self.schedule_reload ()
  File "/usr/share/gnome-schedule/mainWindow.py", line 304, in schedule_reload
    data = self.crontab.read ()
  File "/usr/share/gnome-schedule/crontab.py", line 438, in read
    array_or_false = self.parse (line)
  File "/usr/share/gnome-schedule/crontab.py", line 604, in parse
    success, ver, title, desc, output, display, command_d = self.get_job_data (job_id)
  File "/usr/share/gnome-schedule/crontab.py", line 690, in get_job_data
    return True, ver, title, desc, output, display, command_d
UnboundLocalError: local variable 'display' referenced before assignment
```

---

### Post by jodawe on 2009-11-02
I get the same error after upgrading to 9.10.

---

### Post by mocha on 2009-11-22
This is a known bug for Jaunty to Karmic upgraders.

Just do this:

```
mv /home/USER/.gnome/gnome-schedule /home/USER/.gnome/gnome-schedule.old
```

then run it again, your original crontab tasks should still be there.

For the root crontab tasks, do the same thing above except it's located at "/root/.gnome/gnome-schedule"

---

