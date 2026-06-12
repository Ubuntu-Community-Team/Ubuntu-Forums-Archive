---
title: "Boots into Nautilus . . . I think"
date: 2012-03-22
forum: General Help
---

### Post by cascader on 2012-03-22
Hello . . .

Being somewhat adventurous and somewhat naive at the same time I had a fiddle around with compiz-manager . . . and promptly appeared to lose the Unity desktop . . . well I think that's what has happened . . .

Now my computer boots into Nautilus - that's all I get on the monitor, the Desktop with the (Nautilus)Menu bar at the top and no buttons to close it. No Dash, no panels, nothing.

From a different tty I launched Compiz-Manager and found that the Unity option was de-selected. I selected the Unity option, rebooted (from a different tty) but have had no joy - every time I reboot it's back to Nautilus . . . I am completely flummoxed by this one . . . can anybody shed any light on what's going on.

Thanks, Cascader
BTW - I am not using Gutsy Gibbon as my entry states - I am using the latest Ubuntu 11.10 (I think)(can't get into that computer)

---

### Post by chipbuster on 2012-03-23
Wait, you're booting into your file browser?? Or did you mean GNOME?

---

### Post by kazztan0325 on 2012-03-23
Hi @cascader,

It seems the phenomenon is partly similar to the one which has discussed on following thread.

**[ubuntu] Can see the nautilus menu in Desktop when using Gnome Shell**
[http://ubuntuforums.org/showthread.php?t=1934039]("http://ubuntuforums.org/showthread.php?t=1934039")

I guess maybe @markbl's solution on the thread would help you.

As for disappeared Unity, what about trying this:
```
unity --reset
```

---

### Post by cascader on 2012-03-23
Thanks [COLOR="Blue"]chipbuster[/COLOR] . . . apologies if I haven't been clear . . . to be honest I have not been sure as to what is happening . . . I am new to Unity and haven't read enough (or smart enough :rolleyes:) about it to know whether it runs on top of Gnome or as an independent environment . . .

And thank you [COLOR="blue"]kazztan0235[/COLOR] - your entry solved my problem . . . I have rebooted since applying the fix you suggested and it is again working fine - phew . . .

I am determined to hang in there with Ubuntu and the Unity desktop - it is an impressive OS, but it is foreign to me and without the help of you good ppl I would be stuffed . . .

[COLOR="Red"]Regards, Cascader[/COLOR]

---

### Post by kazztan0325 on 2012-03-23
You are welcome, cascader!

I'm glad to hear you have solved the strange phenomenon.

By the way, it seems "Ubuntu 12.04 LTS" has no such strange things.
However it is still 'Beta 1' at present...

See you somewhere else in this forums!

---

