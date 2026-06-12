---
title: "'%' Activates 'Set Title' Dialog in gnome-terminal"
date: 2011-02-05
forum: General Help
---

### Post by Githlar on 2011-02-05
I've been having an issues recently, every time I try to type the '%' key in gnome-terminal I get a dialog box asking to set the title of the window. This is quite annoying as I'm often switching between jobs in bash.

I've traced the problem down to an entry in the gnome configuration:
/apps/gnome-terminal/keybindings/set_window_title = percent
The strange thing about this key is it's different than the others - it has no owner, description, long description or schema attached to it. I can't for the life of me figure out where it came from!

When I delete this entry everything works as expected. The only problem is: it comes back every time I restart! I have never had an issue with the gnome configuration, so I'm not really sure where to start looking for this issue. Could somebody give me some guidance on where I might locate this trouble entry?

---

### Post by Habitual on 2011-02-06
Can you change it to something besides "%" and will it keep after reboot?

---

### Post by Githlar on 2011-02-06
I have not rebooted since I last deleted the key. I was going to follow your advice and re-add the key with a different value (blank), but lo and behold it was there again with a value of 'percent'! What could be going on here? There must be something that's adding this key. I'd like to know where this key could be written on the disk (I've seen some files in .config or .gnome2 or some other hidden folder that has a bunch of key/value pairs for use with gconf, but I can't recall where) so that I may take it out or maybe even figure out what (if any) application is adding this key? It's quite annoying as I do a lot of work in the terminal as I said earlier.

I did go ahead and change it to blank though to see if it comes back... we'll see.

---

### Post by Githlar on 2011-02-06
Well, that was way easier than I thought. Previously I had done a search of my home directory to try to find any files with 'percent' in the content and I came back with a bunch of stuff, but nothing useful (and it took a LONG time). I just got the brilliant idea to check .gconf in root's home folder and there it was! In the file /root/.gconf/apps/gnome-terminal/keybindings/%gconf.xml is the text:
```
<?xml version="1.0"?>
<gconf>
	<entry name="set_window_title" mtime="1297053730" type="string">
		<stringvalue></stringvalue>
	</entry>
</gconf>
```

Question is, how did it get there? Is there a way to search package contents from the terminal to determine which package wrote this file?

I think I recall seeing a 'contents' file from a package I had installed, but I don't recall where.

---

### Post by Habitual on 2011-02-07
Most likely in that location it is the system default and was installed with the system.

---

