---
title: "Start multiple terminals and have them run commands"
date: 2010-12-17
forum: General Help
---

### Post by jbritz on 2010-12-17
Currently I use the following command to open open a number of terminal windows with tabs at various locations. 

```
gnome-terminal --load-config=/path/to/config/AllTabs
```

My problem is that I want several of the tabs to run different commands on launch.  I haven't even been able to find any real documentation on the --load-config parameter so I'm not sure how to get this working.

---

### Post by Brandon Williams on 2010-12-17
In the section of the config that describes the tab, add a line to describe the command. For example, if you want the tab to run the command "tail -f /var/log/syslog", then the configuration block for the tab might look like this:```
[Terminal0x9edd000]
ProfileID=Default
Command='tail' '-f' '/var/log/syslog'
WorkingDirectory=/home/user
Zoom=1
Width=80
Height=24
```
Notice that each individual argument in the Command value is quoted, which allows for embedded whitespace.

---

### Post by jbritz on 2010-12-17
Fantastic.  Thanks a lot.

Is there a link to some documentation on the load-config?  I haven't been able to find any and would like to look through it.

---

### Post by Brandon Williams on 2010-12-17
I don't think there's any documentation about that option (there's a launchpad bug related to the lack of documentation, anyway). What I did to figure it out was to run a complex command line like "gnome-terminal -e 'some command' --tab -e 'some other command' --tab -e 'yet another command'" and then I ran "gnome-terminal --save-config filename" to figure out what the resulting config would look like.

---

