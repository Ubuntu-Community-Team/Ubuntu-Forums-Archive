---
title: "Macbuntu - Apple logo on login screen"
date: 2011-04-16
forum: General Help
---

### Post by erick404 on 2011-04-16
I've installed Macbuntu 10.10 and found it pretty nice.
However, I don't like using Apple's logo, it seems somewhat silly to me, I'm only interested in the overall appearence. During the installation, I chose the Ubuntu logo wherever I was asked, but it seems I didn't have a choice for the login screen.
How can I remove that bitten apple?
I found that I can set a new logo in Ubuntu Tweak, but I have no idea where to find the original Ubuntu logo file.

---

### Post by Krytarik on 2011-04-16
If a custom login icon gets set, usually a directory in "/var/lib/gdm/.icons" gets created that contains those icon and overrides the default icon of the icon theme set for the login screen. So, to revert the login icon to the default, you just need to remove those directory, most likely the directory is LoginIcons (name of the set icon theme), but we will do a more generic approach here, just in case:
```
sudo rm -rf /var/lib/gdm/.icons
```Note that the parent directory, "gdm", and most of its subdirectories are only readable by root (and gdm).

Greetings.

---

### Post by erick404 on 2011-04-18
My gdm folder was empty. However, I managed to find the icons that Macbuntu uses after using locate LoginIcons.

With Ubuntu Tweak, I set the Ubuntu login icon from /usr/share/icons/LoginIcons/apps/64

---

### Post by Krytarik on 2011-04-18
> **erick404 said:**
> My gdm folder was empty.That's why I said:
> **Krytarik said:**
> Note that the parent directory, "gdm", and most  of its subdirectories are only readable by root (and gdm).

> **erick404 said:**
> However, I managed to find the icons that Macbuntu uses after using locate LoginIcons.

With Ubuntu Tweak, I set the Ubuntu login icon from /usr/share/icons/LoginIcons/apps/64
Anyway, glad that you found another way to fix that issue.

---

### Post by erick404 on 2011-04-19
> **Krytarik said:**
> That's why I said:

[QUOTE=Krytarik]
[I]Note that the parent directory, "gdm", and most  of its subdirectories are only readable by root (and gdm).
[/I][/QUOTE]

Actually, I checked it with sudo ls, and it was indeed empty.

---

### Post by Krytarik on 2011-04-19
> **erick404 said:**
> Actually, I checked it with sudo ls, and it was indeed empty.
That's because all subdirectories/files in there are hidden, like it's also the case with most of your own home directory. So, use "ls -al" instead.

---

