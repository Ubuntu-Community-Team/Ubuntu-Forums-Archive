---
title: "How to kill a stuck program that is blocking the entire display?"
date: 2010-03-09
forum: General Help
---

### Post by Kurtosis on 2010-03-09
Hi all, I've installed UNR on my Asus EeePC 1000HE and love it.  I like the interface, especially overlaying the Desktop with a much more useful and organized full-screen menu system.  It also runs much better than WinXP, not surprisingly.

However, some programs I've downloaded from the Ubuntu Software Center tend to crash.  The geneaology program GRAMPS is the most recent one, though a few others have too.  The problem is they block most or all of the screen, can't be closed with the X or right-click->Close, and they block out most of the Terminal window so I can't sudo kill -9 it.

Is there any other way to kill a frozen program in UNR?  Thanks!

---

### Post by wojox on 2010-03-09
Can you switch to a different console Ctrl+Alt+F1?

---

### Post by sailthesea on 2010-03-09
If you can add items to your control panel add Force Quit and use that to kill misbehaving apps ;)

---

### Post by d3v1150m471c on 2010-03-09
A little trick I used when I ran default ubuntu. Navigate to system > preferences > keyboard and make a hotkey for xkill.
The command will be:
```

xkill

```
This will kill whatever window you click on and then restore your cursor back to normal. Another trick to use, if this fails, is to open tty1 via ctrl+alt+F1 and then login. After you login type in:
```

top

```
then after you find the process press ctrl+c to kill "top". then:
```

pkill theprocessname

```
Than press ctrl+alt+F7 and that should clear things up. You could also hotkey system monitor which works just the same as the task manager in microsoft windows.

---

### Post by Kurtosis on 2010-03-10
Thanks everyone, totally forgot about virtual terminals, force quit, and hotkeys.  Much appreciated!

---

