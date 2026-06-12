---
title: "How can I load Firefox with &quot;undecorated&quot; window?"
date: 2011-05-15
forum: General Help
---

### Post by SteveDee on 2011-05-15
Firefox is auto started on our little netbook, and I am making the most of the small screen by auto-hiding the task bar, and keeping menus & tools to a minimum.

Undecorating the window also helps, but I can't find a way to do this automatically when Firefox loads. Any ideas?

---

### Post by lovinglinux on 2011-05-15
You can add a rule in Compiz to not add decorations to Firefox.

I am not using Compiz right now, but look for "Decoration windows" or something like that in the compiz plugins.

---

### Post by SteveDee on 2011-05-16
Thanks for the input.

As I'm running Lubuntu I want to keep it light, so I'm looking for a simple solution (although I did try DevilsPie which did not work).

However, after reading up on OpenBox I found the answer was indeed simple, and just involves adding the following text to the applications section of /home/{user}/.config/openbox/lubuntu-rc.xml
```

<applications>
   <application name="firefox-bin">
   <decor>no</decor>
   <application>

</applications>

```

For other applications you need to find the application name by running in a terminal:-
```

obxprop | grep "^_OB_APP"

```

Don't use xprop (as I did initially) because the information given is not suitable for OpenBox.

---

### Post by The__Doctor on 2012-12-12
> **SteveDee said:**
> 
```

<applications>
   <application name="firefox-bin">
   <decor>no</decor>
   <application>

</applications>

```

I believe that's a typo. The second <application> should be </application>

---

### Post by lisati on 2012-12-12
Thank you for your contribution, Doctor, it looks correct. It is possible that your Tarids was set to materialise in the wrong year: it is possible that the poster has since discovered another solution or merely forgotten about this thread. It is also possible that something else has changed as well. :D

Old thread closed.

---

