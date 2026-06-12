---
title: "Wine isn't in Applications menu"
date: 2010-05-22
forum: General Help
---

### Post by theozzlives on 2010-05-22
This may be elementary to some, and prolly should to me. Quiet awhile ago I took off wine and deleted EVERYTHING wine from my /home. Now I want to try wine again, and I know it's installed, but it don't show up in applications. I've tried "edit menus > revert" but that don't work. I hear wine has made some progress and don't want to format my /home partition. HELP, please

---

### Post by ronnielsen1 on 2010-05-22
Just reinstall it

sudo apt-get install wine

---

### Post by themusicalduck on 2010-05-22
Reinstalling Wine might help, but you need to use the command ```
sudo apt-get remove wine
``` before ```
sudo apt-get install wine
```

But that command installs the stable wine, the newer wine is package wine1.2.

You could do it from synaptic or software centre too.

---

### Post by theozzlives on 2010-05-23
Still no dice.

---

### Post by mc4man on 2010-05-23
maybe take a look in ~/.config/menus for a file 'applications.menu'

If you see something like this then carefully remove just what's in red (it's almost impossible to show actual formating in post 

```
        <Menu>
		<Name>wine-wine</Name>
		[COLOR="Red"]<Deleted/>[/COLOR]
       </Menu>
```

---

### Post by theozzlives on 2010-05-23
> **mc4man said:**
> maybe take a look in ~/.config/menus for a file 'applications.menu'

If you see something like this then carefully remove just what's in red (it's almost impossible to show actual formating in post 

```
        <Menu>
		<Name>wine-wine</Name>
		[COLOR="Red"]<Deleted/>[/COLOR]
       </Menu>
```

Cool, that was it, thanks!

---

