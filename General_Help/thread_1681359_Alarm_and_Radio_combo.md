---
title: "Alarm and Radio combo"
date: 2011-02-04
forum: General Help
---

### Post by Shade0o on 2011-02-04
I want to make an alarm clock that runs a radio at a certain time but not sure on how to get the alarm clock to open a radio mms link that is already saved.

[http://alarm-clock.pseudoberries.com/](http://alarm-clock.pseudoberries.com/)
[http://radiotray.sourceforge.net/](http://radiotray.sourceforge.net/)

So far I have "radiotray mms://87.117.228.28/pulzar" in the custom command within alarm clock, this does work however it shows up as 'unknown radio'. I would like a way to start the link that is saved if possible.

---

### Post by ronnielsen1 on 2011-02-04
Edit

---

### Post by ronnielsen1 on 2011-02-06
I tried quite a few times to figure this out. It would be simple if you could figure out the command that radiotray uses to turn on

---

### Post by Habitual on 2011-02-06
create this script:

~/radio_alarm.sh
```
#!/bin/bash
radiotray mms://87.117.228.28/pulzar
```

chmod 700 radio_alarm.sh

In alarm-clock:
Green + sign adds...
Scheduled...

On the Notification tab:
"execute command or shell script" is checked
Preferences button:
/path/to/radio_alarm.sh

BTW: I got the "error" unknown radio using the shell script, but it also played the station.
I edited my ~/.local/share/radiotray/config.xml and set "<option name="enabled_notifications" value="true"/>"
to "<option name="enabled_notifications" value="false"/>" to get rid of the nasty notifications.


This [page]("http://linuxsoftware.blogsome.com/2010/04/22/development-towards-06/") suggests that the player can be further manipulated through DBUS
but that I'll leave to your quest.

HTH.

---

### Post by Shade0o on 2011-02-12
Thanks for all your help, And that website helped!

---

### Post by Habitual on 2011-02-13
Glad it worked out.

---

