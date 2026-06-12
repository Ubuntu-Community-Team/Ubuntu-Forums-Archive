---
title: "Adding preformatted text to bashrc"
date: 2010-11-29
forum: General Help
---

### Post by Nozone on 2010-11-29
Hi all,

I was wondering whether anyone knows how to add preformatted text to the bashrc file? I'm ashamed to say I did already read this somewhere but had no use for it and as such forgot it! I'm possibly googling the wrong keywords, so apologies if it's an easy answer to find (with the right keywords!).

Just for completeness, the reason I'm doing my bit introducing my partner to linux, and I've 'embedded' a terminal on her desktop, I want to now add a little ASCII animal with a welcome message (I'm ok with getting the welcome message and colors sorted), much like the one seen in Linux Mint.

All your help is greatly appreciated

---

### Post by dandnsmith on 2010-11-29
I don't know how much this will help:

Mint uses a call to a perl script which uses sprintf calls to construct the cow (or whatever).
The output used is purely text, so you could simply include it in the bashrc - but you might need to invent your own script to call to get over the need to put several lines each time the call will be invoked.

Myself, I went straight for the guts and eliminated the call, as I prefer an unmessed presentation

---

### Post by Nozone on 2010-11-29
Hey again dandnsmith,

Thanks for your help, I had a bit of a play around whilst I was in work and I've managed to achieve what I was aiming for using \n newline for anyone that is curious. It took some trial and error but eventually I managed to get what I wanted.

I'll work on your suggestion too as knowledge is power!

---

