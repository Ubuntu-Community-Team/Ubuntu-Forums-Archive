---
title: "Xrandr &quot;kills&quot; compiz"
date: 2010-04-30
forum: General Help
---

### Post by Ivan.Calderon on 2010-04-30
I have an integrated intel gma945 card. It has a max_texture_size of 2048.

Everytime i try to attach an external monitor and configure it with xrandr, compiz falls back to metacity. 

This is the command im running:
> xrandr --output LVDS1 --mode 1280x800 --pos 0x0 --output VGA1 --mode 800x600 --pos 0x800

It doesn't exceed the texture limit yet compiz gets disabled.

Also > xrandr -qAutomatically extends my desktop, AFAIK it shouldn't happen.

Sorry about my english.

](*,)  :x

Btw, this is a fresh 10.04 x86 install

---

### Post by Xzenome on 2010-04-30
This isn't perfect, but I do this:

```
killall compiz.real && xrandr ... && compiz
```

I hope this helps.

---

### Post by Ivan.Calderon on 2010-04-30
> **Xzenome said:**
> This isn't perfect, but I do this:

```
killall compiz.real && xrandr ... && compiz
```

I hope this helps.

Well, it's perfect for me. Thanks ;)

Resuming it to a little script
> #!/bin/bash
killall compiz.real
xrandr --output LVDS1 --mode 1280x800 --pos 0x0 --output VGA1 --mode 800x600 --pos 0x800
compiz

---

