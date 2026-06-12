---
title: "Binding gnome-terminal"
date: 2011-04-29
forum: General Help
---

### Post by jepperstone on 2011-04-29
I just upgraded to Natty early today.

I have <Ctrl><Super> (CTRL+Windows key) bound to open Dash, which works just fine.

However, when I try to bind <Super> to open gnome-terminal, it doesn't work. I tried this in the Control Center and the windows key doesn't register. I tried opening terminal manually and using gconf-editor > apps > metacity > global_keybindings and I typed in <Super> for run_command_terminal and it still doesn't work. I also tried <Super L>.

I even tried just plain <Super> for opening Dash and that works. I also tried binding dash to <Ctrl><Alt><Shift> (something that doesn't use <Super>) and that works fine. Again, under all these conditions I can't get terminal to pop up when I bind it to <Super> using gconf-editor or Control Center. ](*,)

Any ideas?

p.s. what's the deal with zeitgeist?:twisted:

---

### Post by imigueldiaz on 2011-04-29
> **jepperstone said:**
> I just upgraded to Natty early today.

I have <Ctrl><Super> (CTRL+Windows key) bound to open Dash, which works just fine.

However, when I try to bind <Super> to open gnome-terminal, it doesn't work. I tried this in the Control Center and the windows key doesn't register. I tried opening terminal manually and using gconf-editor > apps > metacity > global_keybindings and I typed in <Super> for run_command_terminal and it still doesn't work. I also tried <Super L>.

I even tried just plain <Super> for opening Dash and that works. I also tried binding dash to <Ctrl><Alt><Shift> (something that doesn't use <Super>) and that works fine. Again, under all these conditions I can't get terminal to pop up when I bind it to <Super> using gconf-editor or Control Center. ](*,)

Any ideas?

p.s. what's the deal with zeitgeist?:twisted:

I believe to have seen some place on Compiz config (I'm supposing you are on Unity) that binds <Ctrl><Alt><T> to Terminal... You can try to investigate it installing ccsm package


Best

---

### Post by jepperstone on 2011-04-29
Still doesn't work through CCSM. Any other suggestions? Narwhal's dash opens up just fine when I have it bound to <Super> or <Ctrl><Super>. If I go to Control Center > Keyboard Shortcuts and try to click a new shortcut for "Run a Terminal", I can bind any key combination except those having to do with the windows (<Super>) key.

---

### Post by mc4man on 2011-04-29
The super to open dash is the default for unity. Unity uses the super quite a bit, I believe it's reserved those binding to some extent.

The default for a terminal is Ctrl+Alt+t, though it comes thru the gnome compatibility plugin in ccsm

By default the bind box may be empty, doesn't need to be filled in though you can (just can't show disabled.

Thru the 6 months of testing natty I did have a few occasions when screwing around in keyboard shortcuts messed a few binding up 
( you could temporarily create a new user, login to it and see how the natty/unity defaults work there.

---

