---
title: "Can't switch keyboard layout"
date: 2010-05-08
forum: General Help
---

### Post by markogts on 2010-05-08
Hello, first post here. 

I have a Karmic 32-bit cleanly installed on a desktop PC. I need to switch often between keyboard layouts, so I installed the keyboard indicator applet. Everything worked fine for a while, I switched between USA-IT-SI-GER layouts with just one click. But suddenly I realized I couldn't switch layout anymore, neither by clicking on the applet, nor hitting the proper key combination (alt+alt gr) nor even going into the menu system>preferences>keyboard. Whenever I reach the keyboard setting menu, I see the various layout, I click on the line with a new layout but nothing changes, layout remains the same. 

I searched a lot before posting here: it seems lot of people have similar problems, but not this one. There are people who can only switch with one of the above mentioned methods, or people who can't switch at login, but in my case things are different: I can switch at login, but then this layout appears to be unmodifiable for the whole session.

Tried to edit the xorg.conf file as explained here [http://ubuntuforums.org/showthread.php?t=798555](http://ubuntuforums.org/showthread.php?t=798555)

>   Option        "CoreKeyboard"
      Option        "XkbRules"    "xorg"
      Option        "XkbModel"    "pc105"
      Option        "XkbLayout"    "us,it,si"to no avail (absolutely nothing happened).  Tried to change between "none-ibus-scim" in the language support menu, nothing changed either. Don't know what to try now.

Any ideas?

---

### Post by markogts on 2010-05-12
Nobody?

---

### Post by Sabir V on 2010-05-23
Have you tried to remove & re-add the keyboard indicator on the panel? I suffered from your problem earlier & this cured it!

---

### Post by simosx on 2010-05-23
There have been some updates in how keyboard layouts work in newer versions of Linux, and you need to follow the new rules. AFAIK, these changes can be found in the release notes.

1. SCIM has been replaced by IBus (pre-installed). If you installed SCIM, you probably makes things more complicated. Remove SCIM and any relevant files.
2. For the layouts you mention you do not need complex input support. Therefore, do not select 'IBus' in the Language Support dialog. In fact, leave it empty, so that the default GTK+ IM is used.
3. You mention that you installed the 'keyboard indicator' applet. In recent Linux (with GNOME 2.30), the 'indicator' appears automatically if you have selected more than one keyboard layouts. So, you do not need to install something special. You can the second layout (and so on) from System/Preferences/Keyboard.
4. Adding layouts in xorg.conf is the wrong way; there are some rules on how those values interact with the values in the gconf settings.

What I suggest is to try to revert any changes you made and use the standard way of specifying keyboard layouts.

Failing that, you can try to reinstall, then use System/Preferences/Keyboard to add the layouts. In addition, set the shortcut for switching between layouts in the Options. If things work, please report back.
If things do not work, please report back with the result of

gconftool -R /desktop/gnome/peripherals/keyboard/kbd

which we can use to verify whether there is a bug somewhere.

---

### Post by markogts on 2010-05-27
Thank you for the help. I solved by upgrading to 10.04, now everything works fine. However, before that, I did manually add the layouts to the keyboard configuration, but without improvement. No idea what it was.

---

