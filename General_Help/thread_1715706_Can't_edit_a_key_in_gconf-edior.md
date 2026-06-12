---
title: "Can't edit a key in gconf-edior"
date: 2011-03-27
forum: General Help
---

### Post by swift100 on 2011-03-27
Hi,

would someone know how to unlock a key for editing? I've changed /apps/nautilus/desktop/computer_icon_name from <no value> to 1 by mistake and since then the Type and Name fields are grayed out when I want to edit it. Same thing with the home folder setting. Tried putting <no value> back but it sets it to 0. If it stays 0 when I want to select apps/nautilus/desktop/computer_icon_visible the system start playing on me. I've changed it using gconftool-2 to string <no value> and at least I can put the icon on the desktop, still the key is grayed out for editing...

thanks!

---

### Post by drs305 on 2011-03-27
In gconf-editor did you actually set the *string* to "<no value>"? That would make the value "<no value>".

You should be able to right click on the entry and select "Unset" and the value should be returned to the original (i.e. nothing). You may need to exit that 'folder' and return to see it actually reflect the '<no value>' setting.

```
gconf-editor /apps/nautilus/desktop/computer_icon_name
```

---

### Post by PCNetSpec on 2011-03-27
The reason you can't change it back to <no value> is because a section similar to this:

> <dir name="desktop">
				<entry name="computer_icon_name" mtime="**[COLOR="blue"]1301266427[/COLOR]**" type="int" value="0"/>
			</dir>

has been added to **/etc/gconf/gconf.xml.defaults/%gconf-tree.xml**

you would need to remove that section ([COLOR="DarkRed"]**after backing up of course**[/COLOR])

and also edit **~/.gconf/apps/nautilus/desktop/%gconf.xml**

and change the entry:

> 	<entry name="computer_icon_name" mtime="**[COLOR="blue"]1301269451[/COLOR]**" schema="/schemas/apps/nautilus/desktop/computer_icon_name" type="string">
		<stringvalue>Computer</stringvalue>
	</entry>
(or similar)
to:

> 	<entry name="computer_icon_name" mtime="**[COLOR="blue"]1286065507[/COLOR]**" schema="/schemas/apps/nautilus/desktop/computer_icon_name"/>
(or similar)

Then log off and on again.

Now it will be back to <no value> in gconf-editor and not greyed.

Tested in a VM.

***_[COLOR="DarkRed"]NOTE[/COLOR]_*** - The numbers in **[COLOR="Blue"]blue bold[/COLOR]** *may* be different on your system... you can get the correct number from the other keys in ~/.gconf/apps/nautilus/desktop/%gconf.xml

---

### Post by swift100 on 2011-03-28
[SIZE=2]Thanks for your answers. I'll try what you suggest after work.

@drs305: what I had done was that in the GUI gconf by mistake I changed */apps/nautilus/desktop/computer_icon_name* to from *<no value>* to *1 *(and it was set as *Integer*). I'd changed only the number 0-1. 

Then having realised this i set 1-0 but it stayed *0* instead of *<no value>*. Tried to type *<no value>* in but it changes to *0*. With such a setting when i tick computer_icon_visible Nautilius starts opening like crazy on the panel until i uncheck the setting. Afterwards it closes down by itself. 

Then i edited this key and noticed that all fields are grayed out except for the value which can be altered. I edited it in gconftool-2 and changed to *string* so i can put *<no value>* which serves as a workaround, meaning that in this setting when i tick *computer_icon_visible* nothing plays up on me and the effect is as it should. Still only gconftool-2 can edit this key.

I had experimented with the "unset" function but what it did it deleted the key (a different one which i'd created in gconftool-2 through a typo). Won't  it delete the whole [/SIZE][SIZE=2]*/apps/nautilus/desktop/computer_icon_name* key?
[/SIZE]

---

### Post by drs305 on 2011-03-28
> **swift100 said:**
> [SIZE=2]I had experimented with the "unset" function but what it did it deleted the key (a different one which i'd created in gconftool-2 through a typo). Won't  it delete the whole [/SIZE][SIZE=2]*/apps/nautilus/desktop/computer_icon_name* key?
[/SIZE]

I would presume that with a key you manually created the 'unset' option might remove it since it didn't exist in the original. That's just my theory though.

For default key, right clicking on a value/key and choosing 'unset' merely returns the value to the original/default setting. It doesn't delete the entire key. It should change the current value of your key ("no string") back to nothing (<no value>). I had to select another key and then return to 'desktop' to see that the change had taken effect.

---

### Post by drs305 on 2011-03-28
Edit: See PCNetSpec's following post. The proposed solution in this post apparently won't work so I've removed it.

---

### Post by PCNetSpec on 2011-03-28
Renaming/deleting **~/.gconf/apps/nautilus** WON'T work, as the key is *now* ALSO stored in **/etc/gconf/gconf.xml.defaults/%gconf-tree.xml**

I'm tempted to consider this a "bug" as it appears to have changed the system defaults without ever having (as far as I can remember) prompted me for a password... though I haven't tried it from a user account that isn't a member of admin... nor did I check if it affected other user accounts.
(I'll test this later and if it does, I'll report it as a bug)

neither will "Unset" work, as it sets it back to whatever is *now* the system default, as stored in /etc/gconf/gconf.xml.defaults/%gconf-tree.xml

As I said, I tested this in a VM, with the same results... folders continually opening in the bottom panel when set as an integer.

One of the first things I tried was renaming stuff in ~/.gconf (including .gconf itself) .. didn't work.

The easiest fix is to just to right-click the computer_icon_name key in gconf-editor and select "New Key..." and create a new key with:
Name: computer_icon_name
Type: String
Value: Computer

This will overwrite the old key (of the same name), but it doesn't fix the greying out of the "Type:" field.

This is fine set as a "String" and greyed, but if for some reason you want it back to default (<no value>), you will NEED to get rid of the added section in
/etc/gconf/gconf.xml.defaults/%gconf-tree.xml

If "before and after" snapshots of those 2 xml files would help, let me know.

---

### Post by PCNetSpec on 2011-03-28
Sorry **drs305** if I stepped on any toes... for some reason this issue caught my attention, so I thought I'd test it. :)

---

### Post by drs305 on 2011-03-28
> **PCNetSpec said:**
> Sorry **drs305** if I stepped on any toes... for some reason this issue caught my attention, so I thought I'd test it. :)

Not at all. We are all here for supporting users having problems. 

I'm glad you took the time to test this issue on a VM.  :-)

---

### Post by PCNetSpec on 2011-03-28
Hmmm... seems **drs305** was probably right, and just renaming the **~/.gconf/apps/nautilus/desktop/panel** directory to something like **panel.old** then logging off and on again, should work after all.

I tried it _again_ in a VM, and this time it made NO changes to:
/etc/gconf/gconf.xml.defaults/%gconf-tree.xml

So I can only assume on my first attempt it still had my password in its recent keyring from a previous "sudo" command.

Apologies to all for any confusion... That will teach me to test things more thoroughly before I open my mouth ;)

---

