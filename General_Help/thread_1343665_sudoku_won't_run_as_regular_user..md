---
title: "sudoku won't run as regular user."
date: 2009-12-02
forum: General Help
---

### Post by ferulebezel on 2009-12-02
For some reason I can run gnome-sudoku from the administrative account, but not from a regular user account.

When I try to run it from a terminal I get this:

```
home:~$ gnome-sudoku
Traceback (most recent call last):
  File "/usr/games/gnome-sudoku", line 67, in <module>
    start_game()
  File "/var/lib/python-support/python2.6/gnome_sudoku/gnome_sudoku.py", line 22, in start_game
    main.start_game()
  File "/var/lib/python-support/python2.6/gnome_sudoku/main.py", line 975, in start_game
    u = UI()
  File "/var/lib/python-support/python2.6/gnome_sudoku/main.py", line 174, in __init__
    if self.select_game():
  File "/var/lib/python-support/python2.6/gnome_sudoku/main.py", line 66, in _
    ret = fun(ui,*args,**kwargs)
  File "/var/lib/python-support/python2.6/gnome_sudoku/main.py", line 187, in select_game
    choice = game_selector.NewOrSavedGameSelector().run_swallowed_dialog(self.swallower)
  File "/var/lib/python-support/python2.6/gnome_sudoku/game_selector.py", line 183, in run_swallowed_dialog
    self.setup_dialog()
  File "/var/lib/python-support/python2.6/gnome_sudoku/game_selector.py", line 75, in setup_dialog
    self.make_saved_game_model()
  File "/var/lib/python-support/python2.6/gnome_sudoku/game_selector.py", line 137, in make_saved_game_model
    durationText = _("Played for %(duration)s") % {'duration': format_time(g['timer.tot_time'],round_at=15,friendly=True)}
KeyError: 'timer.tot_time'

sh: bug-buddy: not found
```

Wha' happen?

---

### Post by Leppie on 2009-12-02
why are you trying to launch gnome sudoku from a terminal?
can't you access it from the main menu?

---

### Post by ferulebezel on 2009-12-02
> **Leppie said:**
> why are you trying to launch gnome sudoku from a terminal?
can't you access it from the main menu?

I just ran it from the terminal so I could get the error messages.  It doesn't run from the menu.  I just get the little "launching sudoku" item on the bottom bar and then it goes away.

---

### Post by Leppie on 2009-12-02
Did you do an upgrade, or has it never worked for your normal account? Is this the only game with this issue?

You could try to completely remove it from your system and then reinstall.

---

### Post by ferulebezel on 2009-12-02
> **Leppie said:**
> Did you do an upgrade, or has it never worked for your normal account? Is this the only game with this issue?

It 9.04 and last upgraded right after installation a couple of days ago.  This is a clean reinstallation.  I had previously upgraded to 9.10 and it broke my video and there was no way to back out of it.

> **Leppie said:**
> You could try to completely remove it from your system and then reinstall.

I've already done that, no change.

---

