---
title: "pidgin - how to UNHIDE (show) buddy icon in chat window?"
date: 2009-08-30
forum: General Help
---

### Post by bluepowder7 on 2009-08-30
on pidgin, when chatting with a contact, in the top right there is a buddy icon - whatever buddy sets as their icon shows up for me to see.  if i right-click on it, i can select "Hide Icon" - but how do i get it back???  i tried right-clicking in the area and searching through menus, but can't find an "Unhide Icon" or "Show Icon" option anywhere.  it's almost as if it's a one-way deal - once the icon is hidden, it's not possible to show it???

anyone know what i can do?

:confused:

here's a pic of one chat window with the icon showing, and the other with the icon missing (either i hid it once or somehow the system isn't showing it)

.

---

### Post by P4man on 2009-08-30
If I hide the icon,  close the chat window, and open a new, its there again.. ?

---

### Post by bluepowder7 on 2009-08-30
> **P4man said:**
> If I hide the icon,  close the chat window, and open a new, its there again.. ?

nope.  restarting pidgin doesn't help either.  i may try to remove / purge / reinstall, but i find that sometimes purge doesn't REALLY purge the configs.

---

### Post by P4man on 2009-08-30
> **bluepowder7 said:**
> nope.  restarting pidgin doesn't help either.  i may try to remove / purge / reinstall, but i find that sometimes purge doesn't REALLY purge the configs.

rather than purging, have a look at them. Piding config files are in ~/.purple
You can edit those XMLs with gedit, perhaps you can see the setting there and solve it?

---

### Post by bluepowder7 on 2009-08-30
> **P4man said:**
> rather than purging, have a look at them. Piding config files are in ~/.purple
You can edit those XMLs with gedit, perhaps you can see the setting there and solve it?

i can see the settings for the contact list and icon, but i can't figure out what the "code" should be - i mean, it ought to be pulling the image from the server / service, so that when my contact updates it on their side, it show the updated one on my side too.

here's a snippet of one of the config XML files (i've XXX'd the names for privacy)

the SECOND buddy is showing his/her icon, and has the massive long 55e860.....png code there along with the icon checksum.  the FIRST buddy doesn't show the icon even though i know he/she has one, and the config file has neither the .png or checksum lines.


```

<contact>
<buddy account='ME_XXX@hotmail.com' proto='prpl-msn'>
<name>BUDDY_1_XXX@msn.com</name>
<setting name='last_seen' type='int'>1251617767</setting>
<setting name='show_offline' type='bool'>1</setting>
</buddy>
	<setting name='gtk-mute-sound' type='bool'>0</setting>
	<setting name='pidgin-infopane-iconsize' type='int'>96</setting>
</contact>

<contact>
<buddy account='ME_XXX@hotmail.com' proto='prpl-msn'>
<name>BUDDY_2_XXX@hotmail.com</name>
<alias>XXXXXXX</alias>
<setting name='buddy_icon' type='string'>55e860ef842cf6577755daa539f8c6651b86d0b1.png</setting>
<setting name='icon_checksum' type='string'>gHCyJvHSWBdHpOjPH+e99I5pwHw=</setting>
<setting name='last_seen' type='int'>1251603527</setting>
</buddy>
	<setting name='gtk-mute-sound' type='bool'>0</setting>
	<setting name='pidgin-infopane-iconsize' type='int'>32</setting>
</contact>

```

---

### Post by P4man on 2009-08-30
Well.. I see one has an icon size of 32 and the other of 96. Have you tried changing that?

Not a very elegant solution either, but perhaps you can remove him/her, and add him/her again?

Either way, this is messing, Id file a bug report at the pidgin developpers or even on launchpad as pidgin is ubuntu supported. You shouldn't have to mess like that.

---

### Post by spinstartshere on 2010-04-05
Did anything ever come of this; does anybody know how to unhide the icons?

---

### Post by amireldor on 2010-07-30
i'm on Pidgin 2.6.2 and after hiding the icon, i closed and then opened the chat window and it reappeared. this is a bit weird but at least the icon is shown again.

---

