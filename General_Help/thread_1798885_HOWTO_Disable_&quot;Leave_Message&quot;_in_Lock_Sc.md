---
title: "HOWTO: Disable &quot;Leave Message&quot; in Lock Screen"
date: 2011-07-06
forum: General Help
---

### Post by 311005901 on 2011-07-06
[SIZE="1"]Note: [This forum post]("http://ubuntuforums.org/showthread.php?t=655475") is a bit outdated and is locked. The file that it refers to has been renamed. This method works for me on Natty.[/SIZE]

[IMG]http://i54.tinypic.com/jv3n6s.png[/IMG]

To de-clutter the Gnome screen lock option for "Leave Message", open Terminal and type the command:
```
gksu gedit /usr/share/gnome-screensaver/lock-dialog-default.ui
```
Then, find the line that says
```
<object class="GtkButton" id="auth-note-button">
```
and edit the next line to say "False".
Note: It's case sensitive.
[IMG]http://i53.tinypic.com/5dqznl.png[/IMG]

---

