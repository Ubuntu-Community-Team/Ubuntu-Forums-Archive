---
title: "command line to view sound card info"
date: 2009-11-30
forum: General Help
---

### Post by ndefontenay on 2009-11-30
Hi.

I need to determine whether my sound card is detected by Ubuntu and being used.

I currently have no sound and I was wondering if I could find out for sure that it is detected. It would help me narrow down the problem. Thanks

Nico

---

### Post by BenAshton24 on 2009-11-30
```
aplay -l
```

---

### Post by RedSingularity on 2009-11-30
Also lspci | grep Audio can be helpful.

---

### Post by BenAshton24 on 2009-12-01
> **RedSingularity said:**
> Also lspci | grep Audio can be helpful.

+1, That's probably more what you're looking for and a lot more specific :P (Although it will exclude a considerable number of sound cards, for example, my SB Live! card doesn't show up because there is nothing about audio in the string "Input device controller: Creative Labs SB Live! Game Port (rev 08)")

you could also do:
```
arecord -l
```
or:
```
cat /proc/asound/cards
```

I can't think of any more :P

---

### Post by ndefontenay on 2009-12-01
If something shows up on my screen that means that ubuntu detects my card and has a driver for it?

If I still have no sound, what does that mean?

---

### Post by JBAlaska on 2009-12-01
Post the output of the above commands here. Also check to see if your sound mixer is muted.

Do this in a term:
```
amixer
```

---

