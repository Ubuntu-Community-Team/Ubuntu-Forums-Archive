---
title: "Mysterious Conky Issue"
date: 2012-01-05
forum: General Help
---

### Post by ahmedh on 2012-01-05
Hi everyone, longtime (X)Ubuntu user here. I have had the same conky setup working for nearly three years now and all of a sudden it decided to crap out on me. I have a startup script that loads two conky instances, one for system monitoring and another with a to-do list and my Google Calendar events. When I restarted my computer today, neither conky instance worked. I tried running conky with either configuration file and this is the output:

```
ahmed@ahmed:~$ conky -d -c /home/ahmed/.conkyrc
Conky: /home/ahmed/.conkyrc: 30: no such configuration: 'on_bottom'
Conky: /home/ahmed/.conkyrc: 63: no such configuration: 'border_margin'
Conky: use_spacer should have an argument of left, right, or none.  'no' seems to be some form of 'false', so defaulting to none.
Conky: /home/ahmed/.conkyrc: 89: no such configuration: 'xmms_player'
Conky: forked to background, pid is 2354
ahmed@ahmed:~$ 
Conky: desktop window (3200095) is subwindow of root window (ad)
Conky: window type - override
Conky: drawing to created window (0x2200001)
Conky: drawing to double buffer

```

Similarly, when I load /.conky_todo, which is the other instance (after killall-ing conky), I get the exact same thing, character for character. Nothing shows up on the desktop in either scenario. I can provide both configuration files upon request, but since the output is identical no matter what I'm inclined to believe that this issue has nothing to do with my configurations. Which means I'm really confused right now. Furthermore, lines 89, 30, and 63 have nothing relevant to the output--eg, line 60 has nothing to do with 'border_margin'. This is the case for both files. Any thoughts?

EDIT: Problem solved by stealing someone's conkyrc and copying over my unique text from before. No idea why that worked.

---

