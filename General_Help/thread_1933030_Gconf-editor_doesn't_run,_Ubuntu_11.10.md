---
title: "Gconf-editor doesn't run, Ubuntu 11.10"
date: 2012-02-28
forum: General Help
---

### Post by Janas on 2012-02-28
Hello,

I'm running Ubuntu 11.10 with the Unity desktop. I want to rearrange the order of the applications in my launcher. I press alt +f2 and enter gconf-editor, click on the gconf-editor application icon. Nothing happens. I've tried it multiple times in slightly different ways. I click on it and it just doesn't do anything.

Can anyone help me?

Thank you.

Edit: Oops, I forgot to add that I am running Unity 2D. Thanks!

---

### Post by Tiganjero on 2012-03-01
Gconf-editor is no longer installed by default in Ubuntu 11.10, meaning you'll have to install it manually:```
sudo apt-get install gconf-editor
```

Cheers,
George

---

### Post by Krytarik on 2012-03-01
> **Janas said:**
> I'm running Ubuntu 11.10 with the Unity desktop. I want to rearrange the order of the applications in my launcher. I press alt +f2 and enter gconf-editor, click on the gconf-editor application icon. Nothing happens. ... I am running Unity 2D.
Both the regular Unity and Unity 2D don't store their settings in GConf, but in DConf; for rearranging *any* Unity 2D Launcher items, please see this guide:

[http://www.tuxgarage.com/2011/10/customizing-unity-2d-ubuntu-natty.html](http://www.tuxgarage.com/2011/10/customizing-unity-2d-ubuntu-natty.html)

Reg. the other matter, apparently being unable to launch Software Center from the Dash to install "apps available for download"; can you launch Software Center directly?

Regards.

---

### Post by Janas on 2012-03-02
It is working now! Thank you!

---

