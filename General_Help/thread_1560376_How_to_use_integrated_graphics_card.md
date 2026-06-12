---
title: "How to use integrated graphics card"
date: 2010-08-24
forum: General Help
---

### Post by Errandir on 2010-08-24
I'm using a lenovo notebook with switchable graphics (Intel HD and ATI Radeon 5650), and I'd like to have Ubuntu use the integrated graphics, but I can't figure out how. The BIOS has two graphics options: switchable and discrete. On discrete just the ATI card runs, but on switchable, it seems like both cards are being used.

Is it possible to use just the integrated graphics?

---

### Post by nacho32 on 2010-08-24
personally I believe you have 1 G-card and that's the ATI

---

### Post by Errandir on 2010-08-24
Do you mean that the integrated graphics mode isn't actually a graphics card? Hmm, I was probably mis-speaking there, sorry. But the question should still be valid, no?

---

### Post by nacho32 on 2010-08-24
you have me confused is this a TV tuner card your talking about ? not sure really what your trying to do, your ATI card is your video. Excuse me if I don't understand

---

### Post by Chris1274 on 2010-08-24
You can disable the ATI graphics card by editing your /etc/default/grub file. Add this command:
```
radeon.modeset=0
```
to the GRUB_CMDLINE_LINUX_DEFAULT line. Be sure afterward to update grub with
```
sudo update-grub
```

---

### Post by Errandir on 2010-08-25
Thanks for the response! Unfortunately, it's still not working. I added "radeon.modeset=0" to the file and it saves fine, but when I run update-grub, it returns "/etc/default/grub: 11: radeon.modeset=0: not found".

Any ideas?

---

### Post by Chris1274 on 2010-08-25
Hmm ... what version of Ubuntu are you using? If you've got legacy Grub instead of Grub2 that might be why it's not working.

You might also try "nomodeset" instead ... doesn't work for me but it might for you.

---

### Post by Errandir on 2010-08-25
I'm using the newest version (10.04 Lucid Lynx). Only installed it a week or so ago. 

As for the command, if you meant to make the line "radeon.nomodeset=0", that returns the same error message as before, so still no luck.

---

### Post by Errandir on 2010-08-26
Anyone?

In case it's relevant, I'm dual booting ubuntu and windows 7. I'm not sure if that affects anything.

---

