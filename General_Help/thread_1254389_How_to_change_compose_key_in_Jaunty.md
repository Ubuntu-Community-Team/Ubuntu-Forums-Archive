---
title: "How to change compose key in Jaunty?"
date: 2009-08-31
forum: General Help
---

### Post by maplon on 2009-08-31
Hi

I want to use the Caps Lock key as the compose key. I had a line in my keyboard section in xorg.conf that accomplished this just fine:
```
Option "XkbOptions" "compose:caps" 
```

The whole keyboard section is now commented out with the note:
```
# commented out by update-manager, HAL is now used
```

I can now go to the Xfce Menu -> Settings -> Keyboard and get a GUI, where I can add different keyboard layouts (like us, gb). Fine.

But in that GUI, can I customize which key is my compose key? If not, where should I now do that?

---

### Post by foresto on 2009-10-22
I don't think XFCE offers a GUI for this, but you can edit /etc/default/console-setup to contain this line:
XKBOPTIONS="compose:caps"
(and then restart X)

For a temporary change, you can run this command:
setxkbmap -option compose:caps

To discover which keys you can use other than Caps Lock, run:
grep compose: /usr/share/X11/xkb/rules/xorg.lst

More info:
[https://help.ubuntu.com/community/ComposeKey](https://help.ubuntu.com/community/ComposeKey)

---

### Post by maplon on 2009-10-23
Great! Thanks. I had found setxkbmap but I didn't know about /etc/default/console-setup. 

Thanks

---

### Post by Agnaramasi on 2010-03-06
On Xubuntu Karmic, editing the XKBOPTIONS line in /etc/default/console-setup has no effect upon restarting X. But this command works immediately, but is impermanent:
setxkbmap -option compose:lwin
To set the compose key permanently, I added the command to my startup list.
But what is the right way to permanently set the compose key in Xubuntu 9.10?
Thanks

---

### Post by hot_franks_49_cents on 2010-05-02
> **Agnaramasi said:**
> On Xubuntu Karmic, editing the XKBOPTIONS line in /etc/default/console-setup has no effect upon restarting X. But this command works immediately, but is impermanent:
setxkbmap -option compose:lwin
To set the compose key permanently, I added the command to my startup list.
But what is the right way to permanently set the compose key in Xubuntu 9.10?
Thanks

I was having similar issues and did some poking around & eventually found [startxfce4(1)]("http://manpages.ubuntu.com/manpages/lucid/en/man1/startxfce4.1.html")*, which would seem to indicate mocking up a **~/.config/xfce4/xinitrc** (you might need to [COLOR="Red"]chmod u+x ~/.config/xfce4/xinitrc[/COLOR] as well) with that line in it.

* the behaviour doesn't seem to've changed from jaunty->karmic->lucid (& why should it've?)

---

