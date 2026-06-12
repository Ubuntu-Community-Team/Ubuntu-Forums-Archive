---
title: "Unity/Launcher problems"
date: 2012-06-21
forum: General Help
---

### Post by Het Irv on 2012-06-21
The default scroll speed for Chromium is a bit slow for me so I found a command that I can run to launch Chromium with the scroll speed set to what I like:
```
chromium-browser --scroll-pixels=155
```

This works great if I run it from the terminal, but I would like to make an icon on my Unity bar to run that command.  I added one using alacarte, which successfully opens Chromium, but at the default scroll speed.  This happens if the launcher is set to "Application" or "Application in Terminal"

What am I missing?

---

### Post by Xernie on 2012-06-21
When you created the menu item, did you include the "--scroll-pixels=155" argument in the "Command" field?

---

### Post by Het Irv on 2012-06-21
> **Xernie said:**
> When you created the menu item, did you include the "--scroll-pixels=155" argument in the "Command" field?

Yes I did, I don't need quotes around the command for it to work do I?

---

### Post by Xernie on 2012-06-21
> I don't need quotes around the command for it to work do I?

No, you don't.

The only other thing I can think of is that maybe you aren't running the launcher item you created. Doesn't Ubuntu make a Chromium launcher item for you when you install it? Why did you have to create a new one? Maybe you are clicking on the one created by default (which wouldn't have the scroll speed thing)?

I know it's a long shot but it's the only thing I can think of.

---

### Post by Het Irv on 2012-06-21
I created a new because I could not find a way to edit the command that ran from Unity.  I saw in another thread where someone suggested using alacarte, and that seemed to work... but this is the first time I have used Unity and I can't find a preferences page for it or anything like that.

---

