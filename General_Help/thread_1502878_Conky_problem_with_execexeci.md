---
title: "Conky problem with exec/execi"
date: 2010-06-06
forum: General Help
---

### Post by weeman7007 on 2010-06-06
Hi, I am running custom scripts in an instance of conky, I was previously using the exec command however realised that this was the cause of the load on my cpu so have switched to execi with a 60 second interval. Since switching to execi it has decided to cut off some of the text at the end.

```
${exec stuffdisp | fold -w43}
```

Is supposed to display a list of games that I want while also making sure that is wraps the text so it is fully readable within conky:

```
1. Naughty Bear - June 8
2. Sniper: Ghost Warrior - June 25
3. Singularity - June 29
4. F1 2010 Sep
5. Brink - Sep 7
6. Two Worlds 2 - Sep 17
7. Test Drive Unlimited 2 - Sep 21
8. Fable 3 - Nov 1
9. Call of Duty Black Ops - Nov 9
10. Fallout New Vegas - Autumn
11. Deus Ex: Human Revolution - 2010
12. HAWX 2 - fall 2010
13. Ghost Recon Future Soldier - Q1 2011
14. Inversion - ??
```

But when using execi it cuts off at 10. Fallout New Vegas - Aut Is there something I am doing wrong?

---

### Post by Brandon Williams on 2010-06-06
I have this problem, too. The only thing I've found that corrects it is to use the minimum_size configuration setting to extend the conky frame down so that it fills up most of the screen's vertical space. On my laptop with a 1400x1050 screen, I set 'minimum_size 280 840', which causes conky to use 20% of the horizontal space and 80% of the vertical space.

The one problem I have with this method is that the blank space that falls within the 280x840 frame is not available as part of the root desktop. If I click with it, the click is not registered. This doesn't bother me when the full space is full of conky output, but when there's a big block of empty space at the bottom of the frame, it can be a little annoying.

---

### Post by weeman7007 on 2010-06-06
hi, it wasn't cutting off right at the bottom, however I have now found a solution, to increase the text buffer size. The default is 256 bit, so I simply doubled it. I hope this solution helps you out as it has with me.

Just insert this at the top of your configuration file:

```
text_buffer_size 512
```

---

### Post by Brandon Williams on 2010-06-09
I forgot about that setting. text_buffer_size is important here too, but it was not enough for me on its own. If I recall correctly, it only limits how much data conky is willing to read from the exec* command. Under some circumstances, you may still lose text at the bottom of the conky display.

---

