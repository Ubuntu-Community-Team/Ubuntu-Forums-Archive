---
title: "How to remap keyboard?"
date: 2012-03-25
forum: General Help
---

### Post by evil gnome on 2012-03-25
Hi,
Please help

I want to have these changes applied to my keyboard. and I want it to be **permanent** and **not** lost when I reboot:

```
keycode 112 = Next NoSymbol Next
keycode 110 = Prior NoSymbol Prior
keycode 115 = Control_R NoSymbol Control_R
keycode 117 = Delete NoSymbol Delete]
```

---

### Post by evil gnome on 2012-03-25
bump...

---

### Post by idoitprone on 2012-03-25
> **evil gnome said:**
> bump...

2 things
first there is a 24 hr bump rule
Wait after 24 hrs to bump

second just put it in a script at boot
if you wanted to make the changes permanent, then it will be a pain since you have to configure alot of settings to make things work in tty and stuff

i believe putting in your home dir and saving those keys  in .Xmodmap will work, some distros are strange you dont ahve to excute xmodmap ~/.Xmodmap to set those keys

[http://cweiske.de/howto/xmodmap/ar01s06.html](http://cweiske.de/howto/xmodmap/ar01s06.html)

here a small guide

---

### Post by lechien73 on 2012-03-25
As far as I know, all keybindings for Lubuntu are stored in the:

```
~/.config/openbox/lubuntu-rc.xml
```

file, so you could try having a look there.

---

### Post by evil gnome on 2012-03-26
> **idoitprone said:**
> 2 things
first there is a 24 hr bump rule
Wait after 24 hrs to bump

second just put it in a script at boot
if you wanted to make the changes permanent, then it will be a pain since you have to configure alot of settings to make things work in tty and stuff

i believe putting in your home dir and saving those keys  in .Xmodmap will work, some distros are strange you dont ahve to excute xmodmap ~/.Xmodmap to set those keys

[http://cweiske.de/howto/xmodmap/ar01s06.html](http://cweiske.de/howto/xmodmap/ar01s06.html)

here a small guide
Sorry about the bump, didn't know the rules I should have read them before posting.

I am somewhat of a noob. already tried some different guides I found in google and did them (all was like save this line to that file and then reboot) but none of them worked.
The link you posted was confusing I didn't figure it out.
Oh BTW I totally forgot, I'm not using Lubuntu anymore (Switched distro just this week), I'm using PeppermintOS Two (Lubuntu based distro).

Please help, the delete key on my keyboard is located at a very unfriendly location and I want to change it.

---

### Post by gsgleason on 2012-03-26
+1 for Xmodmap

---

### Post by idoitprone on 2012-03-26
> **evil gnome said:**
> Sorry about the bump, didn't know the rules I should have read them before posting.

I am somewhat of a noob. already tried some different guides I found in google and did them (all was like save this line to that file and then reboot) but none of them worked.
The link you posted was confusing I didn't figure it out.
Oh BTW I totally forgot, I'm not using Lubuntu anymore (Switched distro just this week), I'm using PeppermintOS Two (Lubuntu based distro).

Please help, the delete key on my keyboard is located at a very unfriendly location and I want to change it.

i been spoiled by kde so i do not know the universal way to do it

[B][https://wiki.ubuntu.com/CustomXSession](https://wiki.ubuntu.com/CustomXSession)

[/B]if i am correct then save the file named

**.xsession** with the contents
```
#!/bin/bash
xmodmap .Xmodmap
```another file named .**Xmodmap **with your custom xmodmap parameters
```
keycode 112 = Next 
 keycode 110 = Prior 
 keycode 115 = Control_R 
add Control = Control_R
 keycode 117 = Delete 


```these links might help
[http://www.acm.uiuc.edu/workshops/cool_unix/xinitrc.html](http://www.acm.uiuc.edu/workshops/cool_unix/xinitrc.html)
[http://old.fluxbox.org/docbook/en/html/app-setup.html](http://old.fluxbox.org/docbook/en/html/app-setup.html)
[http://en.gentoo-wiki.com/wiki/X.Org/xsession](http://en.gentoo-wiki.com/wiki/X.Org/xsession)

when your done dont forget to add excute permission to .xsession
```
chmod u+x .xsession
```

---

