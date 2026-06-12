---
title: "question about Network Manager"
date: 2009-08-23
forum: General Help
---

### Post by Rick Abraham on 2009-08-23
Hi everytime I boot up Network manager pops up asking for my default keyring password. Can I get rid of this pop up ??????????? it's a pain putting my password in everytime.

---

### Post by kelvin.illa on 2009-08-23
There's a work-around for this which involves editing the keyring but... (what I did instead is) just install 'wicd' (**W**ireless **I**nterface **C**onnection **D**aemon). I highly recommended it because it doesn't ask access for the keyring anymore, and installing it automatically replaces Network Manager (which means easy).

wicd is already in the repos but you can update it by going to their site and checking there how to.

oh yeah-- to install:
either:
- in the terminal: sudo apt-get install wicd
- in the add/remove apps: find wicd
- in synaptics: find wicd

---

