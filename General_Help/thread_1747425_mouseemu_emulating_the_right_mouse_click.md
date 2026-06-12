---
title: "mouseemu: emulating the right mouse click"
date: 2011-05-02
forum: General Help
---

### Post by magum on 2011-05-02
[Solved]

Hi @all,

I am one of these macbook users who switched to ubuntu and now slowly tries to get a grip on it.
So to get a little comfortable, I thought it would be nice to have a right mouse click. Well I thought it would be great if I could simulate it on my lower right <Enter> (xev say the keycode is 104).

I googled and googled and ... found mouseemu! And it does exactly this!
BUT it is not working (or at least not for me).

I can edit /etc/default/mouseemu
```
RIGHT_CLICK="-right 0 104"
```and get no effect on the next start up.
(yet ps -A assures me two mouseemu's are up...)

When I try it on the commandline:
```
mouseemu -right 0 104
```I get:
```
mouseemu: can't open /var/run/mouseemu.pid: Permission denied
magum@comp:~$ open: No such file or directory
No uinput device found! Make sure the uinput module is loaded
or CONFIG_INPUT_UINPUT is compiled into the kernel.

```When I try it with "sudo" I get no error message but also no effect.

Could the problem be uinput? But then how would I fix it?

Help appreciated :)

---

### Post by magum on 2011-05-03
TL; DR how do I get mouseemu running?

---

### Post by magum on 2011-05-03
Turns out you cannot trust xev. Showkey returned the key code 96 which works flawless.

The error about uinput can as it seems be ignored.

Solved.

---

