---
title: "How can I change the task bar icons in mail-notification"
date: 2009-07-23
forum: General Help
---

### Post by sefs on 2009-07-23
I just installed the mail notification-package from the repos.

To cut a long story short...the icon is way ugly, and I would like to change it.  See attachment.

Its the brown mail box with the blue arrow.

Is there a way to go about doing this?

Thanks.

---

### Post by Johnny B on 2009-07-23
what icon theme is that?
i cant reproduce that icon

---

### Post by sefs on 2009-07-23
Shiki-Colors.

But the mail-notification is using its own icons not the icon theme in use.

---

### Post by Johnny B on 2009-07-23
i think i've looked everywhere, and i dont have that icon.
it supposed to be somewhere in /usr/share
look in /usr/share/mail-notification
it could be in /usr/share/icons
or run these: (.*g because it could be png or svg)
find /usr/share -name *[Mm]ail*[Nn]otification*.*g
find /usr/share -name *[Ii]nbox*.*g 
find /usr/share -name *[Nn]otification*.*g
find /usr/share -name *[Mm]ail*.*g
find /usr/share -name *[Mm]essage*.*g

sorry i couldnt find it, but i tried...

---

### Post by johnbrondum on 2009-11-21
you'll find it here: /usr/share/icons/gnome/24x24/stock/net

---

### Post by corncob on 2009-11-21
> **johnbrondum said:**
> you'll find it here: /usr/share/icons/gnome/24x24/stock/net

I see it: /usr/share/icons/gnome/24x24/stock/net/stock_outbox.png.  My first thought was to delete it or rename it and then rename the icon you want to 'stock_outbox.png' but those options are grayed out in Nautilus.  I'm sure there's a command line way of doing it but let me check that out.

---

### Post by dcstar on 2009-11-21
> **corncob said:**
> I see it: /usr/share/icons/gnome/24x24/stock/net/stock_outbox.png.  My first thought was to delete it or rename it and then rename the icon you want to 'stock_outbox.png' but those options are grayed out in Nautilus.  I'm sure there's a command line way of doing it but let me check that out.

Make a launcher with this and you will have root access to do things:
```
gksudo "dbus-launch nautilus --no-desktop --browser %U"
```

---

### Post by sefs on 2009-11-22
> **johnbrondum said:**
> you'll find it here: /usr/share/icons/gnome/24x24/stock/net

Blast from the past wow...you actually found it!!!  Good stuff and thanks.  Now I can change that ugly thing.

I found the attached icon on google images, and resized it to 24x24 in Gimp.  Much nicer in my opinion.

---

### Post by corncob on 2009-11-22
> **dcstar said:**
> Make a launcher with this and you will have root access to do things:
```
gksudo "dbus-launch nautilus --no-desktop --browser %U"
```

Good info!  I made a launcher and added the code to my notes.  It gave some errors when run in terminal but it worked.  I had been thinking something along the lines of
```
sudo rm /usr/share/icons/gnome/24x24/stock/net/stock_outbox.png
sudo cp "somethingelse" /usr/share/icons/gnome/24x24/stock/net/stock_outbox.png
```
BTW, is there a command to move a file without using cp and rm?
Anyway, sefs seems to have done what he wanted to do.

---

### Post by sefs on 2009-11-22
> **corncob said:**
> Good info!  I made a launcher and added the code to my notes.  It gave some errors when run in terminal but it worked.  I had been thinking something along the lines of
```
sudo rm /usr/share/icons/gnome/24x24/stock/net/stock_inbox.png
sudo cp "somethingelse" /usr/share/icons/gnome/24x24/stock/net/stock_inbox.png
```
BTW, is there a command to move a file without using cp and rm?
Anyway, sefs seems to have done what he wanted to do.

```

sudo mv "somethingelse" /usr/share/icons/gnome/24x24/stock/net/stock_inbox.png

```

Update [3rd December 2010]:
----------------------------
On one of my systems when I did the above the icon that showed up still was the ugly icon. I do not know why or where mail-notification was pulling it from, as I had replaced the old stock_inbox.png item with a different one.

What I had to do was to browse to "/usr/share/icons/<template-in-use>/"  and create under there the directory structure "24x24/stock/net/" and place my desired stock_inbox.png in there.  Now it works on the problematic system that would not recognize I had made the change in /usr/share/icons/gnome/24x24/stock/net/

---

