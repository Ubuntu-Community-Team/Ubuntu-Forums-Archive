---
title: "locale in tty"
date: 2006-04-26
forum: General Help
---

### Post by uziel on 2006-04-26
I have a small problem with locale in ttys (gnome terminal works fine).

I need to have pl_PL as default locale, but when I merely do

$ LANG=pl_PL

I get a strange effect, that if I type for example "&#281;", then I can backspace, which wipes the &#281; out, but I can backspace once more (and eventually delete whole command prompt recurring this ;])

Also when I establish a ssh connection with external server (which has POSIX locale) I see things like "-r" when typing polish chars.

And... I don't know what to do. Any help?

---

