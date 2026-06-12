---
title: "Tomboy Notes Startup in Background"
date: 2010-04-30
forum: General Help
---

### Post by tareksobh on 2010-04-30
Is there a way to make Tomboy Notes startup in the background when Ubuntu is lunched? I added the command "tomboy --search" to startup applications and whenever Ubuntu starts, Tomboy Notes opens the [Search All Notes] window.

In the previous Ubuntu version, I used to use the Tomboy Notes applet from (Add to Panel) and it used to startup without opening any windows. This method still work on Ubuntu 10.04, but I liked the new icon for Tomboy Notes that appears in the status bar.

Is there a way I can do that?

---

### Post by sharm on 2010-04-30
The --search option is what makes the search window appear.  Just add "tomboy" to your startup items, without --search, and you should be fine.

---

### Post by Raev33 on 2010-05-02
> **sharm said:**
> The --search option is what makes the search window appear.  Just add "tomboy" to your startup items, without --search, and you should be fine.

I have same problem, and I've done that. But at startup the "search window" still opens. The weird thing is, if I run the "tomboy" command in a terminal it starts without the "search window". The command used is the same! Any suggestions?

---

### Post by sharm on 2010-05-04
> **Raev33 said:**
> I have same problem, and I've done that. But at startup the "search window" still opens. The weird thing is, if I run the "tomboy" command in a terminal it starts without the "search window". The command used is the same! Any suggestions?

Either you are accidentally starting Tomboy twice (the second time will cause the Search window to appear), or your panel is taking > 2 seconds to load after Tomboy is started (in which case Tomboy shows the Search window so you can be assured it's actually running).

Accidentally starting Tomboy twice is the most common cause.

---

### Post by Raev33 on 2010-05-05
> **sharm said:**
> Either you are accidentally starting Tomboy twice (the second time will cause the Search window to appear), or your panel is taking > 2 seconds to load after Tomboy is started (in which case Tomboy shows the Search window so you can be assured it's actually running).

Accidentally starting Tomboy twice is the most common cause.

Thanks for the answer. I'm positive that Tomboy is not started twice, so it's probably the > 2 seconds thing. Sounds like a good feature, but in in this particular case it's quite annoying.

---

### Post by overridex on 2010-06-22
> **Raev33 said:**
> Thanks for the answer. I'm positive that Tomboy is not started twice, so it's probably the > 2 seconds thing. Sounds like a good feature, but in in this particular case it's quite annoying.

I had this issue as well, as a quick work around you can create a script like this for example.  I named it delay-tomboy.sh in my ~/bin/ directory.

```

#!/bin/sh
/bin/sleep 5
/usr/bin/tomboy

```

Just run chmod +x on it to make it executable, then choose that as the command in your startup entry instead of tomboy itself.  You might need to play with the sleep time a little depending how long it's taking your panel to load.

-Dan

---

### Post by groggyboy on 2010-11-14
An even more elegant solution:

make your entry in startup applications read "tomboy --quiet".

cheers

---

### Post by sharm on 2010-11-14
> **groggyboy said:**
> An even more elegant solution:

make your entry in startup applications read "tomboy --quiet".

cheers

There is no --quiet option.  That is the same as starting "tomboy" without any arguments.

---

