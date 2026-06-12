---
title: "command to print loaded alsa sound card drivers"
date: 2011-11-16
forum: General Help
---

### Post by hoink on 2011-11-16
What command will tell me the alsa drivers ubuntu (lucid) is using for my two soundcards?

ALSA sound drivers, according to the interwebs, start with 'snd-' and that's the info I need.  What 'snd-blahblah' drivers is ubuntu using to run my cards right now?

When I find those driver names, I can change the driver loading order in hopes to make java applets in firefox use a particular soundcard (sound card, device).  <-- that was added for search engine posterity

[http://alsa.opensrc.org/MultipleCards#How_to_choose_a_particular_order_for_multiple_installed_cards](http://alsa.opensrc.org/MultipleCards#How_to_choose_a_particular_order_for_multiple_installed_cards)

---

### Post by hoink on 2011-11-16
Self-solved.

This process will tell you.

[http://www.calel.org/pci-devices/alsa-device-list.html](http://www.calel.org/pci-devices/alsa-device-list.html)

---

