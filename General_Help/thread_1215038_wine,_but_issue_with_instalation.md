---
title: "wine, but issue with instalation"
date: 2009-07-16
forum: General Help
---

### Post by PsYcHoTiC_MaDmAn on 2009-07-16
I had got wine working earlier (previous thread) but was having issues (it was creating windows too big to fit in the screen (and this is a 23"widescreen running at 1920by1080)

so I removed it, and purged the system of it, it left a menu in the applications bar so removed that via edit menu.

now whichever way I install wine (sudo apt-get install, synaptic packet manager, add/remove applications) it doesnt show up in the menu.

Its not in the edit menu section either

what have I done to bugger it up so

---

### Post by mc4man on 2009-07-16
You could try this
```
 gedit  ~/.config/menus/applications.menu
```

**If** you see this then delete what's in red (maybe also backspace the now empty line, though might not be necessary

```
!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
	<Name>Applications</Name>
	<MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
	<Menu>
		<Name>System</Name>
		<AppDir>/home/doug/.local/share/applications</AppDir>
		<Include>
			<Filename>gconf-editor.desktop</Filename>
		</Include>
	</Menu>
	<Menu>
		<Name>Multimedia</Name>
		<AppDir>/home/doug/.local/share/applications</AppDir>
		<Exclude>
			<Filename>totem.desktop</Filename>
		</Exclude>
		<Include>
			<Filename>totem-xine.desktop</Filename>
		</Include>
	</Menu>
	<Menu>
		<Name>wine-wine</Name>
		<DirectoryDir>/home/doug/.local/share/desktop-directories</DirectoryDir>
		[COLOR="Red"]<Deleted/>[/COLOR]
	</Menu>
</Menu>
```

---

### Post by PsYcHoTiC_MaDmAn on 2009-07-16
mc4man, thank you. got it working again, though it wont let me delete previous programs that I have uninstalled. but I can live with that

---

### Post by mc4man on 2009-07-16
You can probably get those entries removed, though sometimes it's best to leave well enough alone.

The best 1st. step would be to try from edit menus (r.click on Applications or alacarte in terminal.

If you scroll down and expand wine to dir. so the offending programs show up on right side then try a right click -> delete on the entry. Most likely nothing will happen, but then close and reopen Applications -> wine and see if it/they are gone.
(if so and they're removed you'd see an <deleted> entry in the above mentioned file

2nd possibility

Some progs will have a .menu here, if so, deleting it should remove it from the wine menu

~/.config/menus/applications-merged

There also could be leftover folders here though shouldn't affect the menu one way or the other

~/.local/share/desktop-directories

---

