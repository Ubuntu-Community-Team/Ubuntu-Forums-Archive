---
title: "&quot;init 0&quot; works &quot;shutdown&quot; doesn't"
date: 2012-07-04
forum: General Help
---

### Post by rsteinmetz70112 on 2012-07-04
I have a 10.04 LTS install, I chanaged out the motherboard due to a hardware failure. Everything went normally except, when I try to "shutdown" from the GUI the machine restarts, however is a go to a terminal window and "sudo init 0" the machine shuts down as it should. 

It seem obvious that something in Ubuntu is not working quite right but I'm not sure where to begin looking.

---

### Post by msammels on 2012-07-04
Are you using sudo on the shutdown command? Also, have you tried this:

```
sudo shutdown -h now
```

---

### Post by rsteinmetz70112 on 2012-07-04
I had not tried the "shutdown" command in a terminal window. I was referring to the graphical shutdown menu, but now that you mentioned it I have tried 

"sudo shutdown -h now" 

It causes a restart not a shutdown.

---

### Post by msammels on 2012-07-04
Are you on a laptop or desktop?

---

### Post by rsteinmetz70112 on 2012-07-04
Desktop. I just replaced the motherboard because it failed.

---

