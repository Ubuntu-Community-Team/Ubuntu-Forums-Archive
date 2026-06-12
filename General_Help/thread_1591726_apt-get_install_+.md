---
title: "apt-get install + *"
date: 2010-10-09
forum: General Help
---

### Post by Rypervenche on 2010-10-09
When I install any program using "sudo apt-get install" should I add a "-*" after the program name? I believe I remember a friend telling me something about this.

I wanted to install Chromium and I saw that there were some other things with "chromium-" such as codecs. Should I "sudo apt-get install chromium-*"?

---

### Post by MattBD on 2010-10-09
Probably not. * is a wild card - it'll match ANY character - for instance, package* would match package1, package-do-not-install, you get the idea. Instead, try pressing Tab a couple of times and it'll come up with a list of possible things to autocomplete the command with so you can then enter the one you want.

---

### Post by Rypervenche on 2010-10-09
Thanks. It turns out chromium is a dummy package for a game. I won't be using an asterisk when installing :)

---

