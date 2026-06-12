---
title: "Wine folder doesn't appear in gnome menu"
date: 2009-06-29
forum: General Help
---

### Post by trpnblies7 on 2009-06-29
I was having some problems with Wine and wanted to start fresh, so I uninstalled it and deleted my .wine folder in Home. After I reinstalled it, I got a clean .wine folder back, but there's no longer a folder in my Gnome menu for Wine with the options for configuring, opening programs, etc.

Why isn't it there and how do I get it back? I went to the edit menus option to see if the folder was just unchecked, but it's not even listed there.

Thanks.


UPDATE
I fixed it by using an applications.menu.undo file in .config/menus

---

### Post by iswear on 2009-06-30
you can go to the termanal and type winefile and it should come up with something that looks like windows folers.

---

### Post by trpnblies7 on 2009-06-30
That helps a bit, but is there a way to get the Gnome menu entry back so I can launch programs from there?

---

### Post by colau on 2009-06-30
> **trpnblies7 said:**
> That helps a bit, but is there a way to get the Gnome menu entry back so I can launch programs from there?
Did you try System>Preferences>Main Menu ?

---

### Post by trpnblies7 on 2009-06-30
> **colau said:**
> Did you try System>Preferences>Main Menu ?

Yes, but it's not listed anywhere in there.

---

### Post by colau on 2009-06-30
> **trpnblies7 said:**
> Yes, but it's not listed anywhere in there.
```

sudo apt-get purge wine
sudo apt-get install wine

```

---

### Post by trpnblies7 on 2009-06-30
> **colau said:**
> ```

sudo apt-get purge wine
sudo apt-get install wine

```

That didn't do anything either.

The strange part is that the menu entries exist under .local/share/applications, .local/share/desktop-directories, and /usr/share/desktop-directories, but they're just not showing up in my menu.

---

### Post by foxmulder881 on 2010-12-30
I'm experiencing this problem. WINE is installed and working but nothing appears in the Ubuntu or Gnome menu.

---

### Post by tonyrockyhorror on 2011-04-02
I found the answer to this on another forum: edit the file [COLOR=Black]**$HOME/.config/menus/applications.menu**[/COLOR], you should see an entry that looks something like this:
```
<Menu>
    <Name>wine-wine</Name>
    <Deleted />
</Menu>
```Delete the [COLOR=Black]**<Deleted />**[/COLOR] line and that should restore the Wine menu.

---

