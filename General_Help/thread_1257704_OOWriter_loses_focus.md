---
title: "OOWriter loses focus"
date: 2009-09-04
forum: General Help
---

### Post by yeeeev on 2009-09-04
Hi All,

I'm working on a document in OOWriter, but once every few minutes, while I'm typing or moving around the doc, the window loses focus. This is very irritating...
Did anyone see this before? Is there a workaround? Any ideas on how to debug it? Logs? Something??? :)
I'm running Jaunty with OO 3.0.1

Thanks in advance!

---

### Post by P4man on 2009-09-04
do you have a laptop with a touchpad?
These can be a bit flaky under linux in my experience, producing clicks and mouse movement for no obvious reason. if you think that is what you're experiencing, try this:

[http://ubuntuforums.org/showthread.php?t=271052&highlight=disable+touchpad+while+typing](http://ubuntuforums.org/showthread.php?t=271052&highlight=disable+touchpad+while+typing)

---

### Post by yeeeev on 2009-09-04
> **P4man said:**
> do you have a laptop with a touchpad?
These can be a bit flaky under linux in my experience, producing clicks and mouse movement for no obvious reason. if you think that is what you're experiencing, try this:

[http://ubuntuforums.org/showthread.php?t=271052&highlight=disable+touchpad+while+typing](http://ubuntuforums.org/showthread.php?t=271052&highlight=disable+touchpad+while+typing)
I have a touchpad, but I'm not using it (using an external mouse). Other then that, I don't experience this problems with any other application. So I don't think that's it

---

### Post by yeeeev on 2009-09-04
Anyone knows how I can get logs out of OOWriter? I looked at the man and found nothing...

---

### Post by P4man on 2009-09-04
I dont think it logs anything, never mind such a detailed log. However, you can launch OO writer from a terminal, and keep an eye on the output there.

```
ooffice -writer
```

Also, i found this:

[http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=20462](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=20462)

it sounds more serious then your problem (unless you can't type anymore after this happens?) but it does sound quite similar.

---

### Post by Hagar Delest on 2009-09-04
Are you sure it's not the AutoSave feature? When it saves the document, you can't do anything. If you see a green progress bar at the bottom, that's it.

---

### Post by yeeeev on 2009-09-05
Started from terminal with no logs (at least nothing useful).
Upgraded to 3.1, and the problem went away...

---

