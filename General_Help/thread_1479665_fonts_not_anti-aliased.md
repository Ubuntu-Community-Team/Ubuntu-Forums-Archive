---
title: "fonts not anti-aliased"
date: 2010-05-10
forum: General Help
---

### Post by Nightstalker2 on 2010-05-10
I recently went to [this]("http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23") page and tried to follow the instructions. It didn't work, so I decided I would convert back to my theme before that. Ever since then my main fonts (e.g. Arial, Times, etc.) have been gritty and pixellated (as opposed to being anti aliased). I cannot figure out what did it, but it happened after installing the fonts included in that tutorial. I imagine I somehow installed old fonts over new ones or something. Is there any easy way to revert my fonts back to default, as in the way they were before this mishap?

---

### Post by 3rdalbum on 2010-05-10
Oh no.

You just followed a guide for Ubuntu Hardy (version 8.04) on Ubuntu Lucid (version 10.04). That never has a happy ending. You should only follow guides for your version of Ubuntu.

Whatever 'xfonts' packages are installed, try reinstalling them.

Also, in System > Administration > Software Sources, in the Other Software tab, click on the entry for 'awn-testing' and click the Edit button. Change the contents of the 'distribution' field to read "lucid". After exiting the program, run Update Manager.

---

### Post by Nightstalker2 on 2010-05-11
Yea, I made the mistake of assuming that it would be transferable across distros....

I tried reinstalling everything that came up when I typed "xfont" into synaptic. The fonts are still messed up. Is there any way of reverting the fonts on the system back to default?

---

### Post by Nightstalker2 on 2010-05-13
bump

---

