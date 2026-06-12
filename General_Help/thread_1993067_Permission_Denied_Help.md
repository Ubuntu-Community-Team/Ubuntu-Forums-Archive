---
title: "Permission Denied Help?"
date: 2012-06-01
forum: General Help
---

### Post by namone on 2012-06-01
Hey, so I am having permission issues with running a shell file. I have tried running it in "sudo gnome-terminal" but it still denied me.

[HTML]@ubuntu:~/Games/ET$ ./et-sdl-sound
bash: ./et-sdl-sound: Permission denied
[/HTML]

---

### Post by codemaniac on 2012-06-01
> **namone said:**
> Hey, so I am having permission issues with running a shell file. I have tried running it in "sudo gnome-terminal" but it still denied me.

[HTML]@ubuntu:~/Games/ET$ ./et-sdl-sound
bash: ./et-sdl-sound: Permission denied
[/HTML]
on a terminal .
```
chmod +x et-sdl-sound
```

---

### Post by MG&amp;TL on 2012-06-01
Most common cause of that is lack of execution priveleges.

```
chmod +x ./et-sdl-sound
```

should do it. The "chmod +x" bit just sets the execution privileges

Heh, Ninja'd.

---

