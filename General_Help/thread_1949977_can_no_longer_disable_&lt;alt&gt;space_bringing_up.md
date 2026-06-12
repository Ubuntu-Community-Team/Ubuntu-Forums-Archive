---
title: "can no longer disable &lt;alt&gt;space bringing up window menu"
date: 2012-03-31
forum: General Help
---

### Post by Wayne_V on 2012-03-31
Running Ubuntu 12.04 LTS beta with classic gnome desktop.

I have always had the 'activate the window menu' key binding disabled so that I can use <alt>space for keyboard language swapping but after a recent upgrade it started bringing up the menu again (as well as switching the keyboard layout).

System Settings and Compiz Settings GUI's both have the window menu key binding disabled.

gconftool shows the window_menu_key binding disabled as well.

Yet it still seems to be enabled.   Any ideas?

---

### Post by alakra on 2012-04-07
I'm also running into the same issue with one of my Emacs bindings with the new Ubuntu 12.04.  Any luck on this?

  --angelo

---

### Post by Stan Lanning on 2012-05-11
+1

The inability to tailor key-bindings is a true pain for those of us whose fingers have been trained by using Emacs for years.

Is there any hope?  Is anybody listening?

---

### Post by loopum on 2012-05-18
I just found how to do it:
sudo apt-get install compizconfig-settings-manager
Open it, then
 CompizConfig->general options->key bindings: window menu!
disable it!

---

### Post by Wayne_V on 2012-05-20
Doesn't work for me -- I still get the window menu (12.04/Gnome/No Unity)

---

### Post by rjshera on 2012-08-23
I was able to get this working by going to System Settings -> Keyboard -> Shortcuts tab -> Launchers, and changing "Key to show the HUD" to something other than "Alt".  (I changed mine to "Menu" for example).  Of course, you could disable it altogether if you don't care about the new HUD.

Now Alt+Space brings up Gnome Do just fine.

Changing "Key to show the HUD" also has the advantage that when I press "Alt+Left" to go back in my browser that the HUD doesn't annoyingly pop up at the same time.

(Note that I also had previously tried disabling the "Window Menu" keybinding in Compiz, to no effect).  Of course, you'll have to also disable "Activate the window Menu" (or change it to something else) in System Settings -> Keyboard -> Shortcuts as mentioned by the OP.

---

