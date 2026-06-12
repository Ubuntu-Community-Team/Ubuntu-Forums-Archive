---
title: "keychain not invoking gnome-ssh-askpass in Precise?"
date: 2012-05-28
forum: General Help
---

### Post by el_baby on 2012-05-28
Hi,

in my old PC I'm still using Oneiric.

I have a startup script that, when I log in (using xdg and unity) invokes keychain.

If it hasn't been invoked before (e.g. on first login after boot), keychain notices it's running in a gnome environment (and not in a shell), so it invokes gnome-ssh-askpass to ask me for the private key passphrase.

Using the same scripts in Pangolin (fresh install), I never get prompted for the passphrase (so the ssh private key is not added to the keychain).

Does anyone know how to make this work under 12.04?

TIA

---

