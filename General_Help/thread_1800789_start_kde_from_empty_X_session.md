---
title: "start kde from empty X session"
date: 2011-07-09
forum: General Help
---

### Post by enimeizoo on 2011-07-09
Hello,
Well, pretty much everithing is in the title. I have an empty X session running, and I want to run kde inside it. I can run whatever software I want in it, actually (well, I can't move the windows and so, but that is normal), but for some reason, kdm doesn't work.

What I have is a X display and a xterm inside.

here is what I tried :
```
kdm
>Only root wants to run kdm

sudo kdm
>Nothing happened, even though I was propmted for password

service start kdm
>start : Jobis already running : kdm
(it is running, but in another display, and I want two displays anyways, so I won't even try to close the first one)


```I know I can start a new session with kdm in another display from a virtual terminal with 
```
 startx -- :1
```But it is not what I want. I want to open it from inside the X display.

Any helpe is welcome

---

### Post by SeijiSensei on 2011-07-09
Did you try "startkde"?

---

### Post by enimeizoo on 2011-07-09
It works, thanks a lot.

---

