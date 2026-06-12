---
title: "Disabling a plugin in Pidgin."
date: 2009-11-02
forum: General Help
---

### Post by Archbalt on 2009-11-02
I have recently installed the plugin "[Buddy List Options]("http://plugins.guifications.org/trac/wiki/blistops")", which has an option to auto-hide the main menu.

The problem is that, after I've deactivated my account, the plugin just keep the menu hidden and I'm not able to use the Pidgin.

So, since I'm also no longer able to deactivate the plugin from Pidgin, how can I do it without having to reset everything?

Thanks,

Cássius

---

### Post by peculiar penguin on 2009-11-02
Make sure Pidgin isn't running and open your prefs.xml in a text editor

```
kill `pidof pidgin`
gedit ~/.purple/prefs.xml
```Find the line "<pref name='loaded' type='pathlist'>". Directly below you'll see the list of plugins currently enabled. Figure out the file name of the offending one and then delete its line from the file. Make sure to not touch anything else and to keep the XML structure intact. Save the file and restart Pidgin.

---

### Post by Archbalt on 2009-11-02
Worked perfectly. Thanks a lot!

---

