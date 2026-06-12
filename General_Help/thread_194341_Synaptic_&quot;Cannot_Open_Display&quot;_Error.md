---
title: "Synaptic &quot;Cannot Open Display&quot; Error"
date: 2006-06-11
forum: General Help
---

### Post by gendreau on 2006-06-11
Hi,

I'm having a problem which started occurring I *believe* after installing XGL (but not sure it is the cause of my problem) whereby if I click Update Manager or Synaptic Manager from the System Menu, neither will come up.  For a very slight second I can see Update Manager load in the bottom task bar but nothing will come up.

If I run "sudo synaptic" from the terminal, I get the error message, "(synaptic:5901): Gtk-WARNING **: cannot open display:"

I have tried reverting back to before I started using XGL, however it still doesn't seem to work.  I would ideally like it to work under XGL but obviously being able to use Synaptic package manager is more important.

Thank you !!!

P.S. If you want to see any of my files posted, just let me know

---

### Post by Ramses de Norre on 2006-06-11
It's just a guess but can you try if it works when you do ```
xhost + && gksudo synaptic
```

---

### Post by gendreau on 2006-06-11
Thank you, but I get the same error message

---

