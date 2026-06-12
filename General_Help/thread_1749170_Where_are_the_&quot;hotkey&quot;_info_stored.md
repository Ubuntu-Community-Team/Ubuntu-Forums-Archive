---
title: "Where are the &quot;hotkey&quot; info stored?"
date: 2011-05-04
forum: General Help
---

### Post by kjartani on 2011-05-04
Hello.
I have a simulator system running on 10.04lts.

There are some "hotkeys" built in to this system.

eg: Shift+Alt+g starts chrome explorer, Shift+Alt+k shut down the system.

I would like to add some more hotkeys but have no idea of where to save it.

I have to do this in command line.


Regards

Kjartan

---

### Post by vanadium on 2011-05-04
System - preferences - "Keyboard shortcuts" allows you to define and assign hotkeys.

---

### Post by dragonfly41 on 2011-05-04
Also try [COLOR=Blue]autokey[/COLOR] app

[http://www.howtogeek.com/howto/26913/how-to-customize-shortcut-keys-for-any-linux-application/](http://www.howtogeek.com/howto/26913/how-to-customize-shortcut-keys-for-any-linux-application/)

which can associate python scripts with keys

based on the useful AutoHotkey for windows (which can also be installed via wine)

---

### Post by kjartani on 2011-05-04
There is no gnome or kde gui. So I have to do it via command line.

Kjartan

---

### Post by vanadium on 2011-05-05
autokey has a gnome ui, but I am not sure why you should consider autokey at this stage if your system has by default a possibility to configure hotkeys.

---

### Post by kjartani on 2011-05-05
I dont consider Autokey.
But my system already use hotkeys; so someplace this info is stored. But where?

I will try to search for files with text <ctrl> or <alt>. Maybee this will give a result.

Kjartan

---

### Post by Dave_L on 2011-05-05
[ubuntu 10.04]

A custom key I defined is in ~/.gconf/desktop/gnome/keybindings/custom0/%gconf.xml, whose contents are:

```
<?xml version="1.0"?>
<gconf>
	<entry name="action" mtime="1304209443" type="string">
		<stringvalue>/usr/bin/xtrlock</stringvalue>
	</entry>
	<entry name="name" mtime="1304209443" type="string">
		<stringvalue>xtrlock</stringvalue>
	</entry>
	<entry name="binding" mtime="1291544408" type="string">
		<stringvalue>&lt;Control&gt;&lt;Alt&gt;k</stringvalue>
	</entry>
</gconf>
```

That defines Ctrl+Alt+k to perform the command "/usr/bin/xtrlock".

I don't know where the default ones are defined.

---

