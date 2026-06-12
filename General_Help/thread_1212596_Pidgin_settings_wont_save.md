---
title: "Pidgin settings wont save"
date: 2009-07-13
forum: General Help
---

### Post by putnam120 on 2009-07-13
I am trying to edit the keyboard shortcuts in Pidgin 2.4.1

The line that I want to remove or comment out is

```
; (gtk_accel_path "<main>/Conversation/Clear Scrollback" "<Control>l")
```

So I open up the terminal and enter
```
cd ~/.purple
``` then ```
sudo gedit accels
```

Then I change the line to 
```
#; (gtk_accel_path "<main>/Conversation/Clear Scrollback" "<Control>l")
``` or just delete it all together and save.  After which I restart Pidgin. However, when I hit <control> + l it still clears my history, and then when I look at the file the line has reappeared or become uncommented  (I assume that # is how you would comment a line, though I could also try //).

Any suggestions?

---

