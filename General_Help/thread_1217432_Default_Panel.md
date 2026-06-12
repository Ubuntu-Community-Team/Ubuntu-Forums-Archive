---
title: "Default Panel"
date: 2009-07-19
forum: General Help
---

### Post by dsgee on 2009-07-19
I have stupidly deleted the default panel.  Although I can add most, if not all, shortcuts, is there any way I can recreate the default panel without reinstalling Ubuntu?

Thanks,

David

---

### Post by drs305 on 2009-07-19
You can run the following commands:
```

gconftool-2 --recursive-unset /apps/panel  # Resets panels to defaults
killall gnome-panel  # Refreshes panels

```

---

### Post by dsgee on 2009-07-19
Thanks a lot.  I'm completely new to this and so far have failed to follow your instruction properly.  Can you tell me precisely what I type in the command line, including spaces/

Thanks again

---

### Post by drs305 on 2009-07-19
> **dsgee said:**
> Thanks a lot.  I'm completely new to this and so far have failed to follow your instruction properly.  Can you tell me precisely what I type in the command line, including spaces/

Thanks again

Open a terminal either via the menu (Applications, Accessories, Terminal). This is preferred so you can see what is happening in terminal. Or ALT-F2 and in the upper command box type in the commands and hit the Run button. You can also tick "run in terminal".

You can enter the complete line, the part from "#" and after is ignored. It is just a comment to tell you what the command does. You can also just leave it there.

So, open a terminal and enter the following, and then hit the ENTER key. You can hightlight the text, and in the terminal press your middle mouse button to paste the contents. Manually, copy/paste is a bit different from windows. To copy *from* a terminal, CTRL-SHIFT-C. To paste *into* a terminal: CTRL-SHIFT-V.  Copy/paste *outside* of a terminal uses standard CTRL-C and CTRL-V commands - but use the mouse middle button - it's easier!

```

gconftool-2 --recursive-unset /apps/panel

```
Hit enter. It should return the default panel selections.
```

killall gnome-panel

```
Hit enter. It should refresh the panels.

---

