---
title: "start Firefox 7 in Fullscreen mode"
date: 2011-10-24
forum: General Help
---

### Post by tnsmart on 2011-10-24
I need a way for Firefox to launch in fullscreen when started.  I used to accomplish this with the Full Fullscreen add-on, but unfortunately it is no longer compatible with Firefox.

Any ideas?  Thanks.

---

### Post by searchfgold6789 on 2011-10-24
For me, if I close Firefox in fullscreen mode, Firefox will still be in fullscreen mode when I start it up again. To put it into fullscreen just press F11.
 - search

---

### Post by tnsmart on 2011-10-24
> **searchfgold6789 said:**
> For me, if I close Firefox in fullscreen mode, Firefox will still be in fullscreen mode when I start it up again. To put it into fullscreen just press F11.

Thanks for the reply.  I don't want to have to rely on Firefox being in fullscreen mode when it is closed for it to start that way the next time.  I want it to make sure that it starts in fullscreen mode every time.

Does anybody know if the Full Fullscreen add-on will be updated?
Is there a way that I can accomplish this with a script?

Thanks.

---

### Post by tnsmart on 2011-10-25
It looks like the less popular FF Fullscreen add-on works the same as Full Fullscreen and is compatible with Firefox 7.

---

### Post by audwan on 2011-10-25
You may be able to solve this with a small bash script also (stolen from [https://www.linuxquestions.org/questions/linux-software-2/open-firefox-in-fullscreen-f11-mode-hanging-707461/):](https://www.linuxquestions.org/questions/linux-software-2/open-firefox-in-fullscreen-f11-mode-hanging-707461/):)

1. Create a script called firefox-fullscreen.sh (in ~/bin/ or something) that does the following:
#!/bin/bash
/usr/bin/firefox &
sleep 2
xdotool key "F11"

2. Create a launcher (i.e. shortcut) on your desktop that executes the command:
firefox-fullscreen.sh

---

