---
title: "Dual monitors: possible to tty and GUI simultaneously?"
date: 2012-03-20
forum: General Help
---

### Post by williamfisher on 2012-03-20
Hi,

I have searched for a while and from my (very basic) understanding, I don't think this is possible. However, I thought I'd ask just in case:

Is it possible to simultaneously run a tty and a GUI on separate monitors?

Thanks,

William

---

### Post by Paddy Landau on 2012-03-21
Once X Windows is running, it controls the I/O.

Why don't you just open a terminal on the other monitor?

You can, of course, SSH into the computer from a different computer and use the TTY from there, but that's not what you are asking.

---

### Post by jwbrase on 2012-03-21
> **williamfisher said:**
> Hi,

I have searched for a while and from my (very basic) understanding, I don't think this is possible. However, I thought I'd ask just in case:

Is it possible to simultaneously run a tty and a GUI on separate monitors?

You can likely do it with some type of [multiseat configuration]("http://en.wikipedia.org/wiki/Multiseat_configuration"), but I don't think it would be possible with stock Ubuntu.

---

### Post by jerome1232 on 2012-03-21
> **Paddy Landau said:**
> 
Why don't you just open a terminal on the other monitor?


I agree, just full screen a terminal, hide the menu bars and scrollbar if you want to get really crazy.

---

### Post by williamfisher on 2012-03-21
Paddy Landau: Of course opening a terminal on the other monitor would replicate the effects - by asking I meant to probe more about the possibilities of Linux rather than how to achieve the same results. Both of which you clarified for me; thank you!

jwbrase: Multiseat configuration looks like a very close hit too, thanks!

---

### Post by Paddy Landau on 2012-03-21
You can also flip between the two states. In Linux, you have seven consoles, numbered 1-7. You get to each one with Ctrl-Alt-F#. The one with X Windows is number 7. Go ahead and try it: Ctrl-Alt-F3 (say) to go to TTY 3; do whatever you want; then Ctrl-Alt-F7 to return here.

---

