---
title: "Can't delete gnome panel"
date: 2010-06-27
forum: General Help
---

### Post by Johannlynx on 2010-06-27
i'm not sure if i'm posting in the right place if is not i'm sorry.
my problem is that i have tried all what i have found on the net to delete my gnome panel 'cause now i'm using awn 

i just dunno what to do it always starts up when i restart my laptop
i'm running ubuntu 10.04
:confused:

i have been trying for around 2 hours searching but all i try nothing works.
if i kill it it re-spawns 

i tried this
gconftool-2 --type=list --list-type=string --set /desktop/gnome/session/required_components_list '[windowmanager,filemanager]'

also this
gconftool-2 --type=string --set /desktop/gnome/session/required_components/panel 'avant-window-navigator'

but nothing works it always comes back

hope someone can help me
thanks in advance

---

### Post by feelshift on 2010-06-27
You can install Ubuntu Tweak (not in the repository). As far as I remember, it allows you to specify what application you use for a panel.

---

### Post by Johannlynx on 2010-06-27
> **feelshift said:**
> You can install Ubuntu Tweak (not in the repository). As far as I remember, it allows you to specify what application you use for a panel.

i already have it installed and also did it from there but gnome doesn't want to go away
:frown:

---

### Post by nothingspecial on 2010-06-27
Simply move gnome-panel out of /usr/bin

keep it though, you might change your mind

```
sudo mv /usr/bin/gnome-panel ~/.panel
```

Then log out and in again. If you want it back

```
sudo mv ~/.panel /usr/bin/gnome-panel
```

Then log out and back in again.

---

### Post by Johannlynx on 2010-06-28
> **nothingspecial said:**
> Simply move gnome-panel out of /usr/bin

keep it though, you might change your mind

```
sudo mv /usr/bin/gnome-panel ~/.panel
```Then log out and in again. If you want it back

```
sudo mv ~/.panel /usr/bin/gnome-panel
```Then log out and back in again.


thanks a lot nothingspecial 
that solved it :)

---

### Post by guitarMan666 on 2010-07-06
In my attempt to follow this guide: [http://spedr.com/5sih8](http://spedr.com/5sih8) [softpedia's Ubuntu Customization guide] I am trying to delete my bottom GNOME panel and retain the top one (making it autohide and transparent).  Clicking "Delete This Panel" brings up the little dialog box with "Cancel" and "Delete" buttons.  Clicking the "Delete" button does nothing.

Any thoughts?  I want the panel easily restored if I find I don't like this so deleting the binaries is really not an option.

---

### Post by lidex on 2010-07-07
> **guitarMan666 said:**
> In my attempt to follow this guide: [http://spedr.com/5sih8](http://spedr.com/5sih8) [softpedia's Ubuntu Customization guide] I am trying to delete my bottom GNOME panel and retain the top one (making it autohide and transparent).  Clicking "Delete This Panel" brings up the little dialog box with "Cancel" and "Delete" buttons.  Clicking the "Delete" button does nothing.

Any thoughts?  I want the panel easily restored if I find I don't like this so deleting the binaries is really not an option.

Just a thought, but have you tried deleting the top panel, then moving the bottom panel into it's place?

---

### Post by tubunu on 2010-10-20
> **feelshift said:**
> You can install Ubuntu Tweak (not in the repository). As far as I remember, it allows you to specify what application you use for a panel.

> **Johannlynx said:**
> i already have it installed and also did it from there but gnome doesn't want to go away
:frown:

You need to uncheck "Complete lockdown of all panels" in In Ubuntu Tweak to be able to delete your panels.

---

