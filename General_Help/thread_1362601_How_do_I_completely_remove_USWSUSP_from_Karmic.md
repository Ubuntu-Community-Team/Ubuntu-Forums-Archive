---
title: "How do I completely remove USWSUSP from Karmic?"
date: 2009-12-23
forum: General Help
---

### Post by martini1179 on 2009-12-23
I made the mistake up upgrading to Karmic from Ubuntu and I'm having a lot of problems. I'm trying to completely remove the uswsusp package that I had installed on Jaunty. I did a complete removal via Synaptic, but there's still a file named uswsusp in /usr/lib/pm-utils/module.d

Can I safely delete this file? 

Is there anything else I need to get rid of to purge my system of uswsusp?

---

### Post by labinnsw on 2009-12-24
Have you tried the "Complete removal" option in Synaptic?

---

### Post by martini1179 on 2009-12-24
> **labinnsw said:**
> Have you tried the "Complete removal" option in Synaptic?

Please read my question before replying. It's only a few sentences, it won't hurt.

---

### Post by labinnsw on 2009-12-24
I deserve that.

> **martini1179 said:**
> Can I safely delete this file?
Yes it is safe to delete the file.

> **martini1179 said:**
> Is there anything else I need to get rid of to purge my system of uswsusp?
No, that should do the trick.

---

### Post by toaste on 2010-01-17
Those files are a part of the pm-utils package and should be left alone. They exist so that pm-utils will call the correct method if tuxonice or uswsusp are installed.

While deleting them shouldn't do any harm for now, if uswsusp becomes the default in the future a dist-upgrade could break hibernate/syspend. You may restore them by reinstalling pm-uitls.

---

