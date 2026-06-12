---
title: "Firefox won't start"
date: 2010-10-02
forum: General Help
---

### Post by sdbrogan on 2010-10-02
In a recently-installed Lucid, Firefox won't start from the launcher or the applications menu.  It won't start from the terminal either, & no error message.  It will start with 'gksudo firefox' though - of course I don't want to run it with root privileges all the time.  I've tried reinstalling it, but it makes no difference.  Has anyone any ideas ?

---

### Post by andrewthomas on 2010-10-02
start it from the terminal 

then post the output of 

```
tail -n 20 /var/log/messages
```

---

### Post by HereInOz on 2010-10-02
Uninstall it completely ('Mark for complete removal' in Synaptic), then delete the .mozilla directory from your home directory, then reinstall firefox.

See if that works.

---

### Post by lesca on 2010-10-03
I met the same problem after upgrading today.
Thanks to Hereln, the problem has been solved!

---

### Post by sdbrogan on 2010-10-03
Thanks - deleting .mozila did the trick.  (I thought selecting 'Completely remove' did that anyway.)

---

### Post by turboraketti on 2010-11-16
This happens everytime I update firefox. Same issue on two different Ubuntu machines. Do anyone know how to solve this without having to wipe all settings (rm -rf .mozilla/firefox)?

I'm about to hand out a Ubuntu machine to a noob friend. I'm afraid that such annoyances may may knock him off Linux ... so a solution would be most appreciated from my side (as a Linux promoter).

---

