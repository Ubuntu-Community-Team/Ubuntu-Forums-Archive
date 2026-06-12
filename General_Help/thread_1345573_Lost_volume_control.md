---
title: "Lost volume control"
date: 2009-12-04
forum: General Help
---

### Post by Kalanac on 2009-12-04
OK, you can't even begin to know how silly I feel but it seems I've lost my volume control and I can't seem to get it back.

This morning I noticed I had two of the speaker icons on my taskbar so I figured I'd remove the surplus one.  However both of them have vanished.  I've looked in the "Add to Panel" and sound menus but I can't find how to add it back (I'm running Karmic with a regular gnome frontend).

Any ideas where I might find it?

---

### Post by sikander3786 on 2009-12-04
That should show up in "Add to Panel". Just type Vol in the search box and should be able to add it to the taskbar. If not let me know because that will be so strange.:D

---

### Post by Zoot7 on 2009-12-04
Run this:
```
gnome-volume-control-applet
```

Then add that to startup applications (system -> preferences -> startup applications) if it's not there already.

---

### Post by Kalanac on 2009-12-04
Oh good grief I'm being a numpty today.  I'd removed the "Notifiaction Area" gizmo from the task bar.  I ran the code Zoot mentioned and it told me it was already running, it was at that point it dawned on me what happened.

*palm face* Doh

Still, thanks for the help folks.  It seems that the volume control gizmo is no longer it's own independent gizmo.

---

### Post by Zoot7 on 2009-12-04
> **Kalanac said:**
> Oh good grief I'm being a numpty today.  I'd removed the "Notifiaction Area" gizmo from the task bar.  I ran the code Zoot mentioned and it told me it was already running, it was at that point it dawned on me what happened.

*palm face* Doh

Still, thanks for the help folks.  It seems that the volume control gizmo is no longer it's own independent gizmo.

It'd dependent on Pulseaudio this time sadly. However if you want it to be truly independent of whether Pulseaudio, I've a guide posted here:
[http://ubuntuforums.org/showpost.php?p=8343644&postcount=40](http://ubuntuforums.org/showpost.php?p=8343644&postcount=40)

---

### Post by mlnease on 2009-12-06
Thanks, All,

I had exactly the same experience as Kalanc (two volume icons in gnome panel), also solved by Kalanac's solution (add 'Notification Area' back to the panel).  I had realised that volume control was no longer independent but hadn't realised that I'd deleted 'Notification Area' along with the duplicate volume control.  By the way, my Skype icon had vanished too, even though the Skype session was active.

Thanks again.

---

