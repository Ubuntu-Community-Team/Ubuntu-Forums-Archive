---
title: "Conky"
date: 2009-10-28
forum: General Help
---

### Post by TheNessus on 2009-10-28
Gnome, Karmic.

Conky periodically kills itself, without notice. anyone encountered such a thing?

---

### Post by VCoolio on 2009-10-28
Do you get useful output if you run conky with a terminal (and wait for it to happen)? Is total_run_times set to 0 (meaning: run forever)? Is conky really dead or is it secretly running but not shown on screen (check with "ps -ef | grep -i [c]onky" )? If the latter is the case, you may have to uncheck the "skip hide taskbar windows" checkbox in compiz > general options. Post your config if the problem persists.

---

### Post by TheNessus on 2009-10-28
> **VCoolio said:**
> Do you get useful output if you run conky with a terminal (and wait for it to happen)? Is total_run_times set to 0 (meaning: run forever)? Is conky really dead or is it secretly running but not shown on screen (check with "ps -ef | grep -i [c]onky" )? If the latter is the case, you may have to uncheck the "skip hide taskbar windows" checkbox in compiz > general options. Post your config if the problem persists.

it is really dead, as I get nothing with "killall conky". It usually (or always) dies when my internet connection is interrupted (wireless), must have something to do with the fact conky monitors it. Nothing on terminal even if I used terminal to start conky with and left open, did indeed die, but nothing showed. 

unchecking the compiz option would annoy me when switching workstations, I'd rather just activating conky again. 

I do get this when starting conky in termnial, may help?

jeff@jeff-laptop:~$ conky
Conky: /home/jeff/.conkyrc: 11: config file error
Conky: border_margin is deprecated, please use window.border_inner_margin instead
Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
Conky: one or more $endif's are missing
Conky: forked to background, pid is 7755
jeff@jeff-laptop:~$ 
Conky: desktop window (20000c9) is subwindow of root window (13f)
Conky: window type - override
Conky: drawing to created window (0x5a00001)
Conky: drawing to double buffer

---

### Post by VCoolio on 2009-10-29
Well, if it´s about interaction with wireless I'm no use. Maybe it helps if you configure conky to monitor internet connection only if it's up, or do you do that already? Also, ask in the big [conky screenshots thread]("http://ubuntuforums.org/showthread.php?t=281865") in the cafe section and again, post your conkyrc with it. In this case the issue may not be in there, but still.

---

### Post by mattgyver83 on 2009-10-31
Im actually having the same problem, i dont want to bloat the post but will link to my post on a prior thread.

[http://ubuntuforums.org/showthread.php?p=8208683#post8208683](http://ubuntuforums.org/showthread.php?p=8208683#post8208683)

It appears other users are having similar issues as well.

---

