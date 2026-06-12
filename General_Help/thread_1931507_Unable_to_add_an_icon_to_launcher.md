---
title: "Unable to add an icon to launcher"
date: 2012-02-25
forum: General Help
---

### Post by susja on 2012-02-25
Hello,
I have an issue to add one icon to launcher. In general it works and I could add it or move to launcher and then check 'Keep in launcher'.
In my case I want to add icon for program /usr/bin/scangearmp . This program starts my scanner. When I execute it from terminal program starts , then I check on 'Keep in launcher'. That's weird because first of this icon does not have right image ( as it used to be before ) and second when I reboot the system I don't see this icon on my launcher anymore.
What could be the problem?
Thanks,
susja

---

### Post by susja on 2012-02-25
> **susja said:**
> Hello,
I have an issue to add one icon to launcher. In general it works and I could add it or move to launcher and then check 'Keep in launcher'.
In my case I want to add icon for program /usr/bin/scangearmp . This program starts my scanner. When I execute it from terminal program starts , then I check on 'Keep in launcher'. That's weird because first of this icon does not have right image ( as it used to be before ) and second when I reboot the system I don't see this icon on my launcher anymore.
What could be the problem?
Thanks,
susja

I noticed that any new icon I place in a launcher it disappears after system reboot. What should be modified to make it permanent?
Thanks
P.S. I'm using Ubuntu 11.10

---

### Post by efflandt on 2012-02-25
Before you can have a launcher remain in the unity bar you first need a launcher.  Someone thought that **alacarte** was installed by default, but it was not on my 11.10.

```
sudo apt-get install alacarte
```Run **alacarte** from a terminal and it will pop up an app to add a launcher to its menus, where you add it probably does not matter.  For Type: you can either try it as **Application**, or if it needs to use a terminal try **Application in Terminal** instead.

Once you log out and log back in, whatever you added to alacarte should show up in **Dash** (top icon) under **More Apps**. Click on your icon and if you did everything properly and it works, you can then right click it in the unity bar and check **Keep in launcher**.

---

### Post by susja on 2012-02-25
Thanks so much,
I'm all set now.
susja

---

