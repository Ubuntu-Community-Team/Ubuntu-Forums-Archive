---
title: "Gibberish on login screen"
date: 2010-03-27
forum: General Help
---

### Post by leonardjensan on 2010-03-27
Hello

I recently installed Ubuntu 9.10 and for a while everything was ok. Then one day suddenly I got some gibberish on the login screen. See attached pic for details. Please help me get rid of this screen.

[IMG]http://www.dogearsetc.com/Photo0140.jpg[/IMG]

Thank you,

Leonard

---

### Post by tkoco on 2010-03-27
> **leonardjensan said:**
> Hello

I recently installed Ubuntu 9.10 and for a while everything was ok. Then one day suddenly I got some gibberish on the login screen. See attached pic for details. Please help me get rid of this screen.


Thank you,

Leonard

Have you tried logging in as yourself using the console window [Ctrl-Alt-F1 keys]?

---

### Post by leonardjensan on 2010-03-27
I haven't tried but that might work. Is there no way to correct what appears on the log in screen?

Thanks,

Leonard

---

### Post by Kevinator on 2010-03-27
I can't really tell much from that picture, but it sort of looks like the fonts are missing (characters replaced with boxes because the intended glyphs aren't available).

When you log in on the terminal you can check installed fonts. I'm not sure what's supposed to be there, or what GDM would use (might depend on the theme), but I see that ttf-dejavu-core and ttf-freefont are part of the default packages (ubuntu-desktop depends on them). You could check whether they are installed with 'aptitude show ttf-freefont ttf-dejavu-core'.

---

### Post by leonardjensan on 2010-03-28
Thanks, both seem to be installed. This is what I get when I run those commands

Package: ttf-freefont
State: installed
Automatically installed: no
Version: 20090104-2
Priority: optional
Section: x11
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 4,272k
Depends: defoma

Package: ttf-dejavu-core
State: installed
Automatically installed: no
Version: 2.29-2
Priority: optional
Section: x11
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 2,646k
Depends: defoma
Conflicts: ttf-dejavu (< 2.20-1)
Replaces: ttf-dejavu (< 2.20-1)

Anything you can suggest. I can work with these boxes but perhaps I could get them to speak in English too...

---

### Post by Kevinator on 2010-03-28
I don't have a lot of suggestions for this. I really don't understand how fonts are dealt with in the *nix world, and I don't know much about GDM themes.

I was going to suggest changing GDM themes (in the hope that it would pop up a "hey, you are missing this font"), but I can't find a way to do that anymore. For some reason the login screen configuration tool has been dumbed down well beyond the point of usefulness. It's infuriating. I really want to insert a string of curse words here because of how stupid this is, but I'll restrain myself.

So I'm out of ideas. Anyone else?

---

### Post by Kevinator on 2010-03-28
It looks like you might be able to get to the login theme selector with these instructions:

[http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html](http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html)

---

