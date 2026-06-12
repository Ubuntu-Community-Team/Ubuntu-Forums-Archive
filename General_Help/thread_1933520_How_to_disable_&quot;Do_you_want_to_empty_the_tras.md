---
title: "How to disable &quot;Do you want to empty the trash&quot; etc message?"
date: 2012-02-29
forum: General Help
---

### Post by Lucas Malor on 2012-02-29
Is there a way to disable the message "Do you want to empty the trash" that pops up when you unmount a device like an USB? I do **not** want to empty the trash, just remove the message. 
I have ubuntu 11.10 with gnome classic.

---

### Post by Lucas Malor on 2012-03-01
up

---

### Post by howefield on 2012-03-01
Try the Nautilus > Edit > Preferences > Behaviour menu

---

### Post by Lucas Malor on 2012-03-01
It doesn't work... I think it remove the confirmation when you empty the trash.
Doesn't  exist a gconf setting for this? :confused:

---

### Post by Deuce1912 on 2012-03-01
I was having the same problem. Never thought to look in nautilus settings.

It worked for me Lucas. I hope you can figure it out.

- Deuce1912

---

### Post by Lucas Malor on 2012-03-25
No, the fact I do **not** want to empty the trash automatically. I want to empty it manually when there's no more empty space on usb drive. So I want to disable the remainder only.

I checked in gconf and it seems there's no setting for this. I think I must hard-code it, but where I must put my hands?

---

### Post by oklokl on 2012-03-25
First
123@123$

mkdir ~/.local/share/.Trash
and
rebooting system.. 


chmod 700 1.sh
1.sh

Click -> Mouse(1.sh bash Create a button)
Desktop

nano 1.sh
or
vi 1.sh

#bin/bash
rm -fr /media/abcd/.Trash-*
rm -fr ~/.local/share/Trash/*
find /media/. -name ".Trash-*" -exec rm -rf {} \;

---

### Post by Lucas Malor on 2012-03-25
> **Lucas Malor said:**
> Is there a way to disable the [COLOR=Red]message[/COLOR] "Do you want to empty the trash" [...]
;)

---

