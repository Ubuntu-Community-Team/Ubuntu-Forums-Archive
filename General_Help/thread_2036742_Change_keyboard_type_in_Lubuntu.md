---
title: "Change keyboard type in Lubuntu"
date: 2012-08-02
forum: General Help
---

### Post by Gonzalo_VC on 2012-08-02
Hi, all. I've recently changed Ubuntu for Lubuntu 12.04 in my netbook. 
I've tried to change the keyboard layout/map to English alt. international, since I need _constantly_ accents.
When I finally managed to do it (you have to click on *apply* even to test the layout), I was extremely disappointed because Lubuntu changes back to standard English keyboard in any reboot! and I have 'a instead of á, that is (one thing among many) what I need.

My machine (Gateway) is has the US normal keyboard. But I installed and am using Lubuntu in another language (Portuguese Brazil) because is the local language were I live!

Any clues how to fix (both meanings) it?
Thanks!

---

### Post by Zvlwab on 2012-08-03
You need to edit the /etc/default/keyboard file. Mine looks like this
```
remco@pc:~$ cat /etc/default/keyboard 
# Check /usr/share/doc/keyboard-configuration/README.Debian for
# documentation on what to do after having modified this file.

# The following variables describe your keyboard and can have the same
# values as the XkbModel, XkbLayout, XkbVariant and XkbOptions options
# in /etc/X11/xorg.conf.

XKBMODEL="pc105"
XKBLAYOUT="us"
XKBVARIANT="altgr-intl"
XKBOPTIONS="compose:ralt"

# If you don't want to use the XKB layout on the console, you can
# specify an alternative keymap.  Make sure it will be accessible
# before /usr is mounted.
# KMAP=/etc/console-setup/defkeymap.kmap.gz
```

You can specify more keyboard mappings in ~/.Xmodmap, you'll have to do a Google search to find out more about this. Mine looks like this (it replaces caps lock with an alternative backspace)
```
remco@pc:~$ cat .Xmodmap 
remove Lock = Caps_Lock
keycode 66 = BackSpace
```

---

### Post by Gonzalo_VC on 2012-08-03
The correct name seems to be us(alt-int)

---

### Post by Gonzalo_VC on 2012-08-03
> **Zvlwab said:**
> You need to edit the /etc/default/keyboard file. Mine looks like this...

XKBMODEL="pc105"
XKBLAYOUT="us"
XKBVARIANT="altgr-intl"
XKBOPTIONS="compose:ralt"
[/CODE]

Sorry. Did'n work :-(  Even putting "alt-int".

Any other suggestion?
Thanks!

---

### Post by Zvlwab on 2012-08-04
I think you need to leave XKBOPTIONS empty.

---

### Post by Gonzalo_VC on 2012-08-06
> **Zvlwab said:**
> I think you need to leave XKBOPTIONS empty.

I did that too, my friend. No way. The system does not remember that setting after rebooting.
Weird!    :???:


I have also an issue with the bar (posted somewhere else): In Lubuntu we cannot use the bar vertically, on the left, for instance. It left the buttons (opened applications) horizontal and more than an inch wide!!??  :confused:

---

### Post by Gonzalo_VC on 2012-08-06
Oops!!:oops:  I did think and rethink and found out something.
What I did wrong the previous time was typing the keyboard type ("int" instead of "intl") and the system didn't recognize the command.

SOLVED by the details, now. I edited the etc/default/keyboard file and changed the default like this:

XKBMODEL="pc105"
XKBLAYOUT="us"
XKBVARIANT="alt-intl"
XKBOPTIONS=""

Now its working fine í ê à ñ 
Thank you all for the tips.

The bottom line is that you have to edit the file as sudo, since doing the change on the Preferences >> LxKeymap only works for the session, and is changed back on reboot.

---

