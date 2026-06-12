---
title: "Gnome-Schedule not working anymore"
date: 2011-04-19
forum: General Help
---

### Post by calande on 2011-04-19
Hello,

When I start Gnome-Schedule, it opens and closed right away. Here's the output:

```
$ gnome-schedule
/usr/share/gnome-schedule/mainWindow.py:158: DeprecationWarning: Use the new widget gtk.Tooltip
  tip = gtk.Tooltips ()
/usr/share/gnome-schedule/mainWindow.py:159: DeprecationWarning: Use the new widget gtk.Tooltip
  tip.enable ()
no crontab for charles
Traceback (most recent call last):
  File "/usr/share/gnome-schedule/gnome-schedule.py", line 74, in <module>
    mainWindow = mainWindow.main(debug_flag, False, pr, manual_poscorrect)
  File "/usr/share/gnome-schedule/mainWindow.py", line 257, in __init__
    self.schedule_reload ()
  File "/usr/share/gnome-schedule/mainWindow.py", line 308, in schedule_reload
    data = self.at.read ()
  File "/usr/share/gnome-schedule/at.py", line 514, in read
    array_or_false = self.parse (line)
  File "/usr/share/gnome-schedule/at.py", line 174, in parse
    if script[-1] == "\n":
IndexError: string index out of range

```

Also before this happened, I tried to add this command to G.S. but nothing happened when I clicked "Add":

```
vlc "rtsp://mafreebox.freebox.fr/fbxtv_pub/stream?namespace=1&service=206&flavour=sd" --run-time="9000" --sout="video.mpg"
```

I reinstalled G.S. but this didn't solve my problem.
Could you help me please?
Thanks! ;)

---

### Post by calande on 2011-04-20
Any idea? :)

---

