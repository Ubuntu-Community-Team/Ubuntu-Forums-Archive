---
title: "incorrect font being used"
date: 2011-08-19
forum: General Help
---

### Post by Sleven7 on 2011-08-19
I'm trying to follow this tutorial:

[http://newshaven.net/how-to-wiki/manually-install-gnome-3-extensions/](http://newshaven.net/how-to-wiki/manually-install-gnome-3-extensions/)

Everything is fine till I get to this CLI command:

./autogen.sh â€“prefix=$HOME/.local â€“ enable-extensions=â€dockâ€

the a with the circumflex is not correct, I don't know what the correct command should look like.

On previewing this post the strange e looking symbol after the â was added after copy/paste.

Does anyone know what this command should be?

---

### Post by oldos2er on 2011-08-19
> **Sleven7 said:**
> I'm trying to follow this tutorial:

[http://newshaven.net/how-to-wiki/manually-install-gnome-3-extensions/](http://newshaven.net/how-to-wiki/manually-install-gnome-3-extensions/)

Everything is fine till I get to this CLI command:

./autogen.sh â€“prefix=$HOME/.local â€“ enable-extensions=â€dockâ€

the a with the circumflex is not correct, 

Shouldn't be there at all, I would think. 

./autogen.sh prefix=$HOME/.local enable-extensions=dock

You're aware that requires 11.04?

---

### Post by Sleven7 on 2011-08-19
Thanks oldos2er

Yes I have 11.04 installed, just this last weekend.  First thing I did was upgrade to Gnome-shell.  I've been installing the extensions manually, thought I would give this way a try.  Thanks again

---

### Post by Sleven7 on 2011-08-19
oldos2er, now I'm even more curious as to what may be happening.

I copied and pasted the command line from your post, 
this is the way it pasted in the terminal:

./autogen.sh prefix=$HOME/.local enable-extensions=*dock

* = strange square symbol with four markings inside

any ideas?

---

### Post by Sleven7 on 2011-08-19
oldos2er, thought I would share.

Found the correct format at [http://live.gnome.org/GnomeShell/Extensions](http://live.gnome.org/GnomeShell/Extensions)

./autogen.sh --prefix=$HOME/.local --enable-extensions="dock"

---

