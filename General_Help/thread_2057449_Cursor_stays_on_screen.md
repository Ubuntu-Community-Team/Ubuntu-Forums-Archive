---
title: "Cursor stays on screen"
date: 2012-09-13
forum: General Help
---

### Post by bobman321123 on 2012-09-13
I installed Ubuntu on an older computer, and when I move the mouse around, the mouse leaves a mark where it has been. 
Is there any way I can fix this?
The computer has a 512+256 of ram, so it isn't _too_ low on memory.
Any ideas?
Thanks,
Josh

---

### Post by ajgreeny on 2012-09-13
Actually that is a bit too low memory for running unity sensibly, but your symptoms sound more like a graphic card/driver problem.  What graphic card do you have?  If you're not sure run ```
lspci
``` or better```
sudo lshw -c display
```

---

### Post by claracc on 2012-09-14
I have an old pIII 1GHz cpu, 512MB ram, lubuntu 12.04 os. And sometimes, when computer is working hardly (installing updates, playing videos) and I move a window in the screen it leaves the mark of the window.

Using sis 630/730, 64 MB graphics card.

I think it can be related to lack of memory in certain cases or the CPU cannot work as quick as graphics demands.

I recommend to use lubuntu in your old computer, it is less demanding and old computers friendly.

Perhaps not a memory item, but an old CPU one.

---

