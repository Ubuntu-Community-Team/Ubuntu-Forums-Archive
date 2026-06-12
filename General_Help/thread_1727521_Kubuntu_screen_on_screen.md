---
title: "Kubuntu screen on screen??"
date: 2011-04-12
forum: General Help
---

### Post by joe montana on 2011-04-12
Hello, I have a question... I have kubuntu installed and for some time I have some kind of a screen on my screen that wont disappear. Its not a widget or anything, its just there???:confused:
You can see it at the screenshot [IMG]http://i54.tinypic.com/20rwm8p.jpg[/IMG]
Any help? Thanx

---

### Post by rosencrantz on 2011-04-12
Why do you think it's not a desktop widget? No configuration handles? Does it change its appearance when you change the plasma theme?
I'd check the entries in ~/.kde/share/config/plasma-desktop-appletsrc
If you haven't tweaked a lot on your desktop, you could also rename the rc file (like old_plasma-desktop-appletsrc), log out and in and see whether it's still there.
Cheers,
rosencrantz

---

### Post by rosencrantz on 2011-04-12
Can you post your Kubuntu and KDE versions (Help->About KDE in any KDE app)? For older KDE versions, it's a different file.

---

### Post by joe montana on 2011-04-12
Kubuntu version is the latest LTS and KDE is Platform Version 4.5.1 (KDE 4.5.1) if that helps. I have to say i`m not an expert in kubuntu or linux at all so be educative with me :))
I will try that from your first post and will see..

---

### Post by rosencrantz on 2011-04-12
Yes, that helps, the filename I gave you is correct. They renamed plasma to plasma-desktop in KDE 4.3, so I had to ask.
If you have trouble figuring out the rc file, attach it to the next post.

---

### Post by rosencrantz on 2011-04-12
Oh, and my first post looks a bit cryptic ;-)
If you rename the rc file, KDE will not find the file and initialise a default one when you log out and in (no total reboot required). 
Assuming your weird container is something put on the desktop by plasma, it should be gone now.
But, being _very_ educative, I'd say it's no bad idea to look at the file first.

---

