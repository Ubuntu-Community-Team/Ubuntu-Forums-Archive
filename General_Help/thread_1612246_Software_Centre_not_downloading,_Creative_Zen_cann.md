---
title: "Software Centre not downloading, Creative Zen cannot thus connect"
date: 2010-11-02
forum: General Help
---

### Post by bazookacoffee on 2010-11-02
Hi guys,

I've been trolling around on the forum to find answer to my problem. I've found many suggestions but so far none have worked, and my Computer Sci friend cannot even fix this, so here goes...

I need some kind of mtp or gnomad2 to let my creative zen x-fi connect with my linux so I can listen to mp3s in peace.

But, if I try to use software manager, nothing downloads. It simply says archive manager as reason for failed download.

I've tried deleting and re-installing the software centre.

I've tried downloading what I need online.

But neither have done anything.

I appreciate any advice. The £160 spent on this mp3 player is looking like wasted money.

---

### Post by mutex023 on 2010-11-02
Have you tried installing the software through Synaptic Package Manager ? Or are you using the Software Centre ?

---

### Post by bazookacoffee on 2010-11-03
Synaptic produces problems too!

''E: Could not perform immediate configuration on 'libattr1'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)''

---

### Post by bazookacoffee on 2010-11-03
When I try to download libattr1, it gets really mad.

---

### Post by mutex023 on 2010-11-03
You could try removing both 'apt' and 'synaptic' and then reinstalling them via the terminal using the 'sudo apt-get remove <pkg name>' and 'sudo apt-get install <pkg name>', command. But be warned, this might remove other dependent packages also, so make a list of these and then you have reinstall them again.

---

