---
title: "Shortcut to partition on panel?"
date: 2011-06-11
forum: General Help
---

### Post by Splat_NJ on 2011-06-11
Running 10.10 and trying to create a shortcut to an already-mounted partition on the panel. I've tried every command line argument I could think of in the "create custom launcher"'s "location" or "comment" textboxes. I've tried using the UUID. I've tried dragging the partition from Nautilus to the panel and that allows me to do that. When I execute the panel shortcut it still errors with no application associated. I tried adding "nautilus" to the command lines but still errors.

Anyone know how to add a shortcut/launcher on the panel to a mounted partition? Thanks.

---

### Post by yetiman64 on 2011-06-11
Right click on the desktop and create a new launcher. 

For the command line try this one,
```
nautilus file:///media/<foldername-partition-is-mounted-in>
```obviously alter <foldername-partition-is-mounted-in> accordingly :).

Name the launcher and give an icon if needed. Move it to somewhere in your home folder. I create a hidden folder called .Launchers on my Lucid install. From there (where it needs to stay) then drag it onto the panel.

---

### Post by Splat_NJ on 2011-06-11
Thanks Yetiman64, but I tried that one, too. No joy yet.

---

### Post by Splat_NJ on 2011-06-11
Well, I must have done something different this time. :confused:  
On my panel I created a custom launcher using "Application" for type, "myBacks" as its name, and "nautilus file:///media/0_Backs" (without the quotes) for the command.  I don't understand why but it's now working. Thanks Yetiman! :KS

---

### Post by yetiman64 on 2011-06-11
Are your "Places" folders OK for opening normally (association wise)?

Edit: we posted at the same time. Good to hear it works. Remember to mark as solved if you're happy with your results :-)

---

### Post by Splat_NJ on 2011-06-11
Yeah, glad you reminded me. I always forget to mark my threads solved until some time later. Thanks again!  \\:D/

---

