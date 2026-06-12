---
title: "Start-up HUGE problem."
date: 2010-03-25
forum: General Help
---

### Post by connorh123 on 2010-03-25
So I downloaded an ATI thing in Add/remove, because I thought it had something to do with my drivers. After I installed it, update manager popped up. I installed the upgrades in there, and it told me to restart later or now. I chose now. After that, I tried to log in, and it never got there. What happened was it goes to the Ubuntu load up screen, then it says my monitor has no signal, and it comes up with a partly fuzzy screen. It does this three times (it goes to the no signal window three times, and it goes to the fuzzy screen three times). When it goes to the fuzzy screen the third time, it stays there. And I can't do anything. The only thing that I can think about fixing this, is to go into sudo, but I don't know which kernal I have. Please help?

---

### Post by Fxy on 2010-03-25
If you can boot into terminal type > sudo apt-get remove <program> changing <program> with the name of what you installed...  This might help, i don't actually know :?

---

### Post by Mark Phelps on 2010-03-25
Sounds like you may have been trying to install ATI drivers that are incompatible with your video card.

Use the directions in the link below to remove them:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

If you're running Ubuntu 9.10, don't bother with creating an xorg.cong file.  Reboot without one and the kernel will automatically install the proper open source drivers.

---

### Post by connorh123 on 2010-03-25
How do I do anything without having terminal? I could probably press esc when it gives me the option, then it gives me the kernal that I'm using. But I don't know that. So what should I do? On the link you gave me, should I be removing?

---

### Post by patchwork on 2010-03-25
When the screen goes fuzzy, try hitting CTRL ALT F1

This should bring you to the tty console.

---

### Post by connorh123 on 2010-03-25
> **patchwork said:**
> When the screen goes fuzzy, try hitting CTRL ALT F1

This should bring you to the tty console.

That didn't work.
This is coming from my moms' computer.
I installed this shown below, my mom uses Karmic. However I'm using Jaunty.
[IMG]http://i43.tinypic.com/2wozlz9.png[/IMG]
After I did that, Update Manager showed up, and installed the stuff in there. I chose to restart now, and now I can't get back on.
Please guys, I need help. I have no idea what to do, and my computer won't go to the log in screen.
Another problem. I think I can solve this if I can get into terminal, but there is absolutely no way to get into it. I tried recovery mode, and tried going into every option. But nothing will let me type a command freely. If I can get into terminal, somehow, I can probably fix this. But without getting to the log in screen, it's very impossible.

---

