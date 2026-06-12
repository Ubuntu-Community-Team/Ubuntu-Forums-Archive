---
title: "Hide windows"
date: 2010-02-05
forum: General Help
---

### Post by littledude565 on 2010-02-05
Hi all, I've decided to get back into Ubuntu after a while and I've installed 9.10 on my laptop. 

And I had a question, is there any program i can use to hide a window of a program with a hotkey? 
For example, say if i was on a messenger program and college or something, and someone walks by. Is there a program that lets me press a combination of keys so that all the windows of the program gets hidden?

Thanks for any help guys ^_^

---

### Post by agnes on 2010-02-05
Not with 1 keypress unless that particular program is always the same program.
If so, you could bind the command "killall <app-name>" to a shortcut via compiz. 

You can change settings (via e.g. Ubuntu Tweak) so that double clicking on the titlebar of a program, "rolls it up"  to make only the titlebar visible, but then, it's still visible as the titlebar and in your panel.

What you also could do is, add a application launcher to the panel with the command "xkill", xkill kills the window you afterwards click on.

Maybe best thing close would be to use multiple workspaces. Then if someone approaches you + the nasty program :P, switch to another workspace with a key command. Make sure via panel settings that in the panel only windows from the current workspace are shown and don't add a "workspace switcher applet"  to your panel. You can also switch the particular window to another workspace. See System->Prefer.->Keyboard Shortcuts

---

### Post by chewearn on 2010-02-05
Ctl+Alt+D

---

### Post by agnes on 2010-02-06
That's not 100% hiding... window will be visible in the panel (assuming one has a window list applet in the panel).

---

### Post by chewearn on 2010-02-06
Ctl+Alt+D is equivalent to clicking "Show desktop" icon on the bottom right.

"killall", "kill", etc command would close the program, instead of hiding it.  Might as well press hotkey for quit in that case (Ctl+Q or Ctl+W depending on program).  No need for elaborate unnecessary hackery.

---

### Post by underquark on 2010-02-06
Have two desktops - a "work" one and a "play" one.  Swap between them with [Ctrl]-[Alt] and arrow keys.

---

