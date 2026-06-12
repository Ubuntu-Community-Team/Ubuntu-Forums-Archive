---
title: "gconf-editor&gt;&gt;metacity&gt;general&gt;button_layout wont get edited ??"
date: 2010-12-11
forum: General Help
---

### Post by rvchari on 2010-12-11
hey guys,
i wish to re arrange the button layout and i went to gconf-editor. the key under metacity> button_layout says its not writable. how do i change permissions and edit according to my wish ?

---

### Post by stinkeye on 2010-12-11
> **rvchari said:**
> hey guys,
i wish to re arrange the button layout and i went to gconf-editor. the key under metacity> button_layout says its not writable. how do i change permissions and edit according to my wish ?

I had the same problem because I had previously set the key as mandatory
and couldn't unset the key as mandatory.

The file that sets the key as mandatory and makes it unwritable is
```
/etc/gconf/gconf.xml.mandatory/%gconf-tree.xml
```

This was my file and only contained the one entry```
<?xml version="1.0"?>
<gconf>
	<dir name="apps">
		<dir name="metacity">
			<dir name="general">
				<entry name="button_layout" mtime="1288083049" type="string">
					<stringvalue>close,minimize,maximize,spacer,menu:</stringvalue>
				</entry>
			</dir>
		</dir>
	</dir>
</gconf>
``` 

I deleted the file, logged out and back in and the key was writable again.

---

### Post by rvchari on 2010-12-21
i came across another way and tat works fine too.
i had to issue command "gksudo gconf-editor" in terminal.
it will ask for admin rights and it opens gconf.
then select File > New Mandatory Window. a new window opens. then i went to apps > metacity > general and i could unset the key from there. after that i opened a new default window, editied the button layout and made that mandatory. it worked !!!
atleast u dont have to search the key, delete it and let it be created on next log in.
i think i can mark this thread as solved !!!

---

