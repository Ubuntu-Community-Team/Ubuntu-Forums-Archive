---
title: "Help me write a quick script, please"
date: 2010-02-15
forum: General Help
---

### Post by dixie460 on 2010-02-15
Howdy all, I am running sensors applet to monitor the temps on my Core 2 Duo processor and my hard drive. I have alarms enabled and I see there is a section where a script can be made to run in the event that an alarm is triggered. The alarm comes up on the screen, but clears when the alarm condition goes away. I would like to know how to write a script that will display a message that will stay on the screen and show the alarm condition until I acknowledge it, even if the alarm clears by itself. Could someone please show me how to do this, and possibly write me a quick sample script?

Also, is it possible to log these events with time/date stamp using a script?

Thanks in advance!!

Regards,
Andy

---

### Post by dixie460 on 2010-02-16
Anyone? I have Googled some things on scripting, but still looking for advice from those who know more than I do...;)

---

### Post by dixie460 on 2010-02-17
Alright!! I got something going here, using one of the example scripts I found in /usr/share/doc/python-notify/examples and modifying it to fit my needs. Here's the code  for a high temp warning on Core 1. I have one each for warnings on CPU, Core 0, Core 1, and /dev/sda. The script will display a message box with OK and Cancel buttons, and the message remains on-screen until either one of the buttons is clicked, even if the alarm condition clears.


```
#!/usr/bin/env python

import pygtk
pygtk.require('2.0')
import gtk
import pynotify
import sys

def default_cb(n, action):
    assert action == "default"
    print "Alarm acknowledged"
    n.close()
    gtk.main_quit()

if __name__ == '__main__':
    if not pynotify.init("Temperature Alert"):
        sys.exit(1)

    n = pynotify.Notification("High temperature alarm has been triggered for Core 1")
    n.add_action("default", "Default Action", default_cb)

    if not n.show():
        print "Failed to send notification"
        sys.exit(1)

    gtk.main()
```Now, I would like to get rid of the Cancel button that is displayed under the warning, and add a time and date stamp to it. If anyone has any advice on making that happen, I'd appreciate the help. :D

---

### Post by dixie460 on 2010-02-18
Alright y'all, after some thinking I realized that I can't make Python write to the system log, and I couldn't find a way to make it display a timestamp in the notification box. My solutiuon which I actually like better is to have sensors applet write to the system log using the logger command. The log already time/date stamps all the entries, so now all I have to do if I come back to my computer and see the notification box waiting for me is check the system log. Now my only desire is to get rid of the Cancel button. I will call this thread solved, and leave it here in case anybody searches for a similar topic. If I figure out how to get rid of the Cancel button, I'll post the update in here too.

Regards,
Andy

---

