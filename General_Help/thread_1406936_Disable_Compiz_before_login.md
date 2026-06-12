---
title: "Disable Compiz before login"
date: 2010-02-14
forum: General Help
---

### Post by Orlsend on 2010-02-14
So I was playing with my compiz with a Intel Graphic card and I enable a effect that caused my graphics to die render my install useless after login, Can I disable compiz before I log in? after I log in all I can do its use ctrl+alt+f2.

Thanks

---

### Post by flippo on 2010-02-14
If you edit ~/.gconf/desktop/gnome/session/required_components/%gconf.xml (i think) you should see your default window manager in there.  If you set it to "metacity" compiz shouldn't launch.  Unless of course you have something replacing the default window manager with compiz, then you have to disable that.

Let me know if it works.

---

### Post by nos09 on 2010-02-14
its easy change your defalt window manager to metacity and compiz would not start.
you can change it by 
edit ~/.gnome/desktop/session/required_components/%gconf.xml

---

### Post by nos09 on 2010-02-14
oops sorry folks didn't seen the second replay...

---

### Post by Orlsend on 2010-02-15
But how do I edit the file? I cant log in!

---

### Post by rnerwein on 2010-02-15
hi
rescue mode - login - change your file - reboot
ciao

---

### Post by Flimm on 2010-02-16
> **Orlsend said:**
> But how do I edit the file? I cant log in!
You can edit Gconf settings from the command line like this:
```
gconftool-2 --set /desktop/gnome/session/required_components/windowmanager --type string metacity
```
If that doesn't work, use a live CD to edit the following file: ~/.gconf/desktop/gnome/session/required_components/%gconf.xml so that it looks like this:
```
<?xml version="1.0"?>
<gconf>
	<entry name="windowmanager" mtime="1266326776" type="string">
		<stringvalue>metacity</stringvalue>
	</entry>
</gconf>
```

---

