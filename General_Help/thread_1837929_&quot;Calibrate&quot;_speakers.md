---
title: "&quot;Calibrate&quot; speakers?"
date: 2011-09-02
forum: General Help
---

### Post by syntr on 2011-09-02
Is there any way to "calibrate" one's speakers in Ubuntu? I recently bought new speakers and around 25% is the loudest I'd ever put them and even that's a little loud. How can I make 30% volume my maximum volume?

---

### Post by hhh on 2011-09-02
Turn the volume knob on the speaker down.

---

### Post by syntr on 2011-09-02
> **hhh said:**
> Turn the volume knob on the speaker down.

I hope you're not planning on quitting your day job in the near future to become a comedian.

As you can see my USB speakers have no volume knob.

[IMG]http://i.imgur.com/2hZbB.jpg[/IMG]

---

### Post by syntr on 2011-09-02
Little bump

---

### Post by hhh on 2011-09-03
> **syntr said:**
> I hope you're not planning on quitting your day job in the near future to become a comedian.
I'll be here the whole week.

In a terminal, run...```
alsamixer
```

Hopefully you will have at least 2 adjustment levels, one for "Master" and an additional one for "Front" (and maybe one for "PCM"). Lower the level for "Front", when you lower or raise your volume applet slider it will only affect "Master".

---

