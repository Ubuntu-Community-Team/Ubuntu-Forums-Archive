---
title: "LÖVE is totally broken for no apparent reason."
date: 2010-07-14
forum: General Help
---

### Post by HOLOGRAPHICpizza on 2010-07-14
I just installed LÖVE (sudo aptitude install love), and I can't get it to load any games. If I start love by its self, I get the "no game" screen, but if I try to load up anything else all I get is a blank screen, with no info at all being printed to the terminal. I even tried making a very simple game (code below) and it still shows a blank screen, with nothing printed to the terminal.
```
function love.load()
        print("Hello World!")
end

function love.draw()
        love.graphics.print('Hello World!', 400, 300)
end
```
Any ideas?

---

### Post by diggan on 2011-02-14
Sorry for bump but almost exactly got the same problem. When I launch LÖVE I get the same screen whatever I do, a spinning planet with LÖVe written in it.

---

### Post by kostkon on 2011-02-14
Try installing the latest version. You can download a deb from its site.

---

### Post by stinkeye on 2011-02-15
According to Pat "Love is a battlefield"

---

### Post by diggan on 2011-02-15
> **kostkon said:**
> Try installing the latest version. You can download a deb from its site.

Tried installing every version I could find before I found out that I didn't make the .love package the right way.

Note to self: Do not exec the main.lua, exec the folder with the main.lua:KS

---

