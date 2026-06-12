---
title: "chromium issue"
date: 2009-10-31
forum: General Help
---

### Post by andymorton on 2009-10-31
Hi, I've just downloaded Chromium. The browser itself is working but I can't get the launcher icon on to the panel. I tried to drage and drop the product_logo_48.png on there but that didn't work. If anyone's got a solution I'd appreciate it.

Thanks. andy

---

### Post by P4man on 2009-10-31
just right click on the launcher in Applications > internet and choose "add this launcher to panel"

The hard way is making a custom launcher and pointing it to chromium-browser %U

---

### Post by andymorton on 2009-10-31
> **P4man said:**
> just right click on the launcher in Applications > internet and choose "add this launcher to panel"

The hard way is making a custom launcher and pointing it to chromium-browser %U

I tried that but Chromium isn't there in the list. :(

---

### Post by P4man on 2009-10-31
> **andymorton said:**
> I tried that but Chromium isn't there in the list. :(

You mean its not in the application menu? How did you install it ? If you installed it from repositories somewhere it should be in Applications > internet main menu. Perhaps try logging out and in, see if that makes it appear.

If you compiled it from source then you'll have to make a custom launcher I imagine. Right click on the panel > add to panel > custom application launcher. Give it a name and description and use the above mentioned 
```

chromium-browser %U 
```

as command. But you shouldnt have to do that normally.

---

