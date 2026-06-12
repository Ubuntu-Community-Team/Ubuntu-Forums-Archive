---
title: "terminal is screwing up"
date: 2009-11-30
forum: General Help
---

### Post by gfunkera on 2009-11-30
when i run commands in the terminal and the command returns to the dollar prompt (i.e. user@machine:~/Desktop$), sometimes that prompt remains hidden until i type something... 

also it will sometimes return with a partial command that i had typed. for instance: when i do a command like "faad LilWayne-IFeelLikeDying.flv" it returns (without converting btw, which is another problem im dealing with lately) "user@machine:~/Desktop$ ying.flv" 

what the heck?!:popcorn:

---

### Post by efflandt on 2009-11-30
Sometimes if you view or output binary files to the screen, they contain codes that are console/terminal escape codes that can change things like making text the same color as background, a wierd font of graphic characters, etc.  See **man reset**.

You may need to hit enter key first, or in some cases if newline has been inadvertently remapped, you might need to hit **Ctrl-J**, then type **reset**, then **Ctrl-J** (Control J is newline or linefeed).

---

