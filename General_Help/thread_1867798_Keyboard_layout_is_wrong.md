---
title: "Keyboard layout is wrong"
date: 2011-10-23
forum: General Help
---

### Post by Ghostlove on 2011-10-23
Hello, me again.

I have a UK keyboard. When upgrading to 11.10 I selected the UK keyboard layout. However now the @ and " keys are the wrong way round (so if I try to type @ I get " and vice versa), as if it thinks I am using a US keyboard.

I'm using 11.10 in 'Classic' mode because I hate Unity, and I can't find anywhere to change this. It's really slowing me down! Does anyone know how I can swap these two keys around?

---

### Post by in·ter·punct on 2011-10-23
[LIST=1]
[*]Applications > System Tools > System Settings > Keyboard
[*]Typing Tab > Layout Settings (bottom left) > Layouts Tab
[/LIST]
From there you can add and remove keyboard layouts.

---

### Post by Ghostlove on 2011-10-23
I've already been there, and it definitely says English (UK).

---

### Post by btindie on 2011-10-23
I'm not sure if it's the same under Oneiric as I'm still using Maverick, but what's in /etc/default/console-setup ?

I've got > XKBLAYOUT="gb"


Also, what if you run gnome-keyboard-properties, does that allow you to correctly set the keymap? Remove the american one so it doesn't get confused and apply system wide.

---

### Post by linuxinstalledfromhdd on 2011-10-23
If you are in a help group for people installing 11.10, but you don't use 11.10, well why should we be installing it too? There is something really messed up about 11.10. Oh well.

> **btindie said:**
> I'm not sure if it's the same under Oneiric as I'm still using Maverick, but what's in /etc/default/console-setup ?

I've got 

Also, what if you run gnome-keyboard-properties, does that allow you to correctly set the keymap? Remove the american one so it doesn't get confused and apply system wide.

---

### Post by cozumel on 2011-10-23
Just to follow on from btindie's post.  I found this on iGrudge.net.  [http://igrudge.net/keyboard-layout-ubuntu-server-11-04/]("http://igrudge.net/keyboard-layout-ubuntu-server-11-04/")
There is an alternative method below the original post in comments.

> I installed Ubuntu Server 11.04, and managed to select the wrong keyboard layout during setup.

To change it to the correct keyboard mapping I had to edit the file /etc/default/keyboard


XKBMODEL="pc105"
XKBLAYOUT="us"
XKBVARIANT=""
XKBOPTIONS=""

The line we have to change is XKBLAYOUT=”us”, where we have to instert our layout instead of us.

When we have changed it to the correct layout, we run sudo dpkg-reconfigure console-setup witch will reload the layout.
I realise is for 11.04 server but hopefully will help you.

Good luck :)

---

