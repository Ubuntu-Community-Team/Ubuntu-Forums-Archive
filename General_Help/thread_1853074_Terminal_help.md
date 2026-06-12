---
title: "Terminal help"
date: 2011-10-01
forum: General Help
---

### Post by spiky001 on 2011-10-01
I have a terminal open and can redirect output to a 2nd terminal```
ls > /dev/pts/2
``` that appears on 2nd terminal ok, But it sits there with the output It wont return to prompt (on 2nd terminal) 1st 1 returns ok, any ideas have to finish off, so it returns to prompt.

---

### Post by prodigy_ on 2011-10-01
Hmm. I'm not sure if there's any way to "return" to prompt on pts2 in this case. In fact, it'd be a bit illogical if this happened because no command is actually being executed in the shell that is attached to this terminal.

In a manner of speaking it's still at the same prompt it was before you redirected the output though the cursor has moved to a different line. Try running a command in pts2 and you'll see that it's working as usual.

---

### Post by noah++ on 2011-10-01
I am guessing all that output is simply moving the printed prompt way back in the scrollbuffer, and that the terminal is actually still responsive to input. Try issuing a command?

---

### Post by papibe on 2011-10-01
As prodigy_ and noah++ have commented, that is just displaying the text on the other terminal, but bash is not receiving any input. In that way, it is similar to the command 'wall'.

If you are really interested in sending commands to another terminal, you need another approach. For example using the program 'screen'. Check my post in this [thread]("http://ubuntuforums.org/showthread.php?t=1843007&highlight=screen"). It's bit more advanced, but it opens a lot of possibilities.

I hope this helps,
Regards.

---

### Post by spiky001 on 2011-10-01
Ok yes running a command dose still work then back to prompt, thks guys I,ll leave thread open just incase, but the replys were good enough.

---

