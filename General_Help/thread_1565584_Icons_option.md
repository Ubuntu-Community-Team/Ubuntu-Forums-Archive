---
title: "Icons option"
date: 2010-09-01
forum: General Help
---

### Post by anxean on 2010-09-01
It's been about 3 years since ive used ubuntu.  Great changes have been made.  My only beef is that I can't find the option to hide icons in menus,  you know when you click applications and see the programs with icons beside them, I don't like that.  There used to be an option to hide icons in menus in the appearance section.  What happened to gnome?! it has changed so much in 3 years..

Thanks in advance

---

### Post by satish_j on 2010-09-01
gconf-editor is the answer..Run it in the terminal.
Navigate to desktop->gnome->interface..there is a key there on right side by the name 'Menus have icons'..
Untick it and the icons in menus will not be shown..
I use it myself as it improves the performance _a bit..._

---

### Post by anxean on 2010-09-01
nice, i should have known that!


I kept messing with it and broke it.

*Could not change key value. Error message:
Can't overwrite existing read-only value: Can't overwrite existing read-only value: Value for `/desktop/gnome/interface/menus_have_icons' set in a read-only source at the front of your configuration path

<stringvalue>small-toolbar</stringvalue>
</entry>
<entry name="show_unicode_menu" mtime="1283343936" type="bool" value="false"/>
<entry name="show_input_method_menu" mtime="1283343936" type="bool" value="false"/>
<entry name="enable_animations" mtime="1283343924" type="bool" value="false"/>
<entry name="can_change_accels" mtime="1283344007" type="bool" value="false"/>
<entry name="menubar_detachable" mtime="1283343630" type="bool" value="false"/>
<entry name="menus_have_tearoff" mtime="1283343629" type="bool" value="false"/>
<entry name="use_custom_font" mtime="1283343520" type="bool" value="false"/>
<entry name="buttons_have_icons" mtime="1283343979" type="bool" value="false"/>
<entry name="menus_have_icons" mtime="1283343616" type="bool" value="false"/>
<entry name="icon_theme" mtime="1283395148" type="string">
<stringvalue>Humanity-Dark</stringvalue>

i used sudo when i got that. file has write access.. wtf i dont want icons!

any ideas would be appreciated.

thanks again
Last edited by anxean; 1 Hour Ago at 12:25 AM..

---

### Post by anxean on 2010-09-01
remove

---

### Post by anxean on 2010-09-01
I kept messing with it and broke it. 

*Could not change key value. Error message:
Can't overwrite existing read-only value: Can't overwrite existing read-only value: Value for `/desktop/gnome/interface/menus_have_icons' set in a read-only source at the front of your configuration path

	<stringvalue>small-toolbar</stringvalue>
	</entry>
	<entry name="show_unicode_menu" mtime="1283343936" type="bool" value="false"/>
	<entry name="show_input_method_menu" mtime="1283343936" type="bool" value="false"/>
	<entry name="enable_animations" mtime="1283343924" type="bool" value="false"/>
	<entry name="can_change_accels" mtime="1283344007" type="bool" value="false"/>
	<entry name="menubar_detachable" mtime="1283343630" type="bool" value="false"/>
	<entry name="menus_have_tearoff" mtime="1283343629" type="bool" value="false"/>
	<entry name="use_custom_font" mtime="1283343520" type="bool" value="false"/>
	<entry name="buttons_have_icons" mtime="1283343979" type="bool" value="false"/>
	<entry name="menus_have_icons" mtime="1283343616" type="bool" value="false"/>
	<entry name="icon_theme" mtime="1283395148" type="string">
		<stringvalue>Humanity-Dark</stringvalue>

i used sudo when i got that. file has write access.. wtf i dont want icons!

any ideas would be appreciated.

thanks again

---

### Post by anxean on 2010-09-06
i reinstalled gnome and now it works

---

