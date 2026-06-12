---
title: "Is there an easy way to black out my monitors?"
date: 2012-08-29
forum: General Help
---

### Post by dadoprso on 2012-08-29
I study at my desk. I like being next to my computer in case I need to use it. But when I'm reading a text book the light bothers me.

I'm using ubuntu 10.04. Is there a way to easily make the screen go black? Without putting my computer to sleep, etc.

Thanks,
Dado

---

### Post by TheFu on 2012-08-29
Set the screen saver to be a blank screen/turn off monitor, then run it?

---

### Post by dadoprso on 2012-08-29
Is there a keyboard shortcut to run screen saver?

---

### Post by dadoprso on 2012-08-29
Also, I dont want to lock my computer

---

### Post by TheFu on 2012-08-29
> **dadoprso said:**
> Is there a keyboard shortcut to run screen saver? You can set one.  In LXDE, that is inside an *~/.config/openbox/lxde-rc.xml *file. I don't know how to do in in other envs, but I've seen a GUI in  Unity.

---

### Post by TheFu on 2012-08-29
> **dadoprso said:**
> Also, I dont want to lock my computer
In LXDE, the screen saver has a toggle to lock the screen or not. Don't check that box if you don't want to lock it.


Google found this solution too: [http://systembash.com/content/how-to-turn-off-your-monitor-via-command-line-in-ubuntu/](http://systembash.com/content/how-to-turn-off-your-monitor-via-command-line-in-ubuntu/)
```
 $ xset dpms force off
```

---

### Post by dadoprso on 2012-08-29
> **TheFu said:**
> You can set one.  In LXDE, that is inside an *~/.config/openbox/lxde-rc.xml *file. I don't know how to do in in other envs, but I've seen a GUI in  Unity.

What folder does ~ refer to?

---

### Post by oldos2er on 2012-08-29
> **dadoprso said:**
> What folder does ~ refer to?

Your home folder. i.e. /home/user/.config/openbox/lxde-rc.xml

---

