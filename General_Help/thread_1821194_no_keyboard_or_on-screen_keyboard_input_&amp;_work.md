---
title: "no keyboard or on-screen keyboard input &amp; workaround"
date: 2011-08-08
forum: General Help
---

### Post by eris23 on 2011-08-08
Running natty.  Main user account.  In Ubuntu & Ubuntu Classic, both gnome, no keyboard or on-screen keyboard input.  Compiz & metacity both bad.  Mouse okay.  Other user accounts okay.  KDE okay.

Tracked problem to /home/{user}/.gconf/desktop/gnome/session/required_components/%gconf.xml.  Removed file, problem goes away.

File contents:

<?xml version="1.0"?>
<gconf>
	<entry name="windowmanager" mtime="1303412016" type="string">
		<stringvalue>compiz</stringvalue>
	</entry>
</gconf>

Anyone, any idea why it didn't work?

---

### Post by drewsus on 2011-08-08
You said the problem went away when you deleted that file... so, what are you asking now?

---

