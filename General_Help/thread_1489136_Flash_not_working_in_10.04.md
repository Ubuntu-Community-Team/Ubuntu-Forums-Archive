---
title: "Flash not working in 10.04"
date: 2010-05-20
forum: General Help
---

### Post by James Crysis on 2010-05-20
Hi,
I just recently installed 10.04. It seems reasonably solid, but I can't get the adobe flash plugin working, so I can't view any embedded flash videos in my browser(using Chrome).
In synaptic I have 'flashplugin-installer' installed. I've tried installing the transitional package in synaptic as well. And I've tried downloading it directly from Adobe's website, but when I do I get the following error after it has downloaded:

"Package 'adobe-flashplugin' is virtual"

I've also tried un-installing/re-installing the flash plugin in synaptic but that doesn't change anything either.
Any ideas? Let me know if you need any more information.

Thanks,
James.

---

### Post by garvinrick4 on 2010-05-20
It is just as easy to install ubuntu-restricted-extras and you get flash all your codecs for playing video's, music and such plus java and a few true type fonts.
```

sudo apt-get install ubuntu-restricted-extras
```

---

### Post by James Crysis on 2010-05-21
Sweet, this worked after a restart. Thanks for the help man it's greatly appreciated.

---

