---
title: "mail-notification appearing at login despite having no entry in Startup Applications"
date: 2010-05-09
forum: General Help
---

### Post by Budoc on 2010-05-09
Despite ridding the startup applications list (System > Preferences > Startup Applications) of any entry containing mail-notification, when I next login to my computer mail-notification starts up again without prompting. 

The reason why I do not want mail-notification to start at login is that it loads before my wireless internet connection is finalized, which results in a flashing error message in the notification panel. Previously in Karmic, I solved this problem by running mail-notification.sh as a startup application:

```
#!/bin/bash

sleep 60 && 
mail-notification --sm-disable &
```

I have verified that this script still works as intended by first running killall mail-notification and then running the above script from a terminal, but upon startup another mail-notification process is automatically loaded from somewhere.

As I fail to see any startup related options in mail-notification itself (right click on icon > properties), and there appear to be no mail-notification related startup entries in System > Preferences > Startup Application, I'd like to know if there are any other locations in ubuntu where programs can be set to startup automatically? I'd like to solely run my mail-notification.sh script that sleeps for 60 seconds so that it starts up after the internet connection is finalized. The version of mail-notification that I am using is a modified version of the one appearing in the lucid repositories (only modified to enable SSL). This problem occurred before the modification was made.

---

### Post by John Bean on 2010-05-09
You may want to remove the indicator-messages package with Synaptic or apt-get. That's what puts the envelope in the indicator applet and has no user configuration options as far as I know - you either remove it or live with it.

---

### Post by Budoc on 2010-05-09
For reasons that I cannot fully explain yet, I had a rogue entry for mail-notification in ~/.config/autostart that persisted irrespective of what I did in System > Preferences > Startup Applications. Expected behaviour is observed fter manually removing this file and rebooting my computer, and then adding my script to the Startup Applications. I'll mark this solved for now.

---

