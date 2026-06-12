---
title: "vi help please"
date: 2011-09-29
forum: General Help
---

### Post by liquidmonkey on 2011-09-29
i have already read a few tutorials on using vi but was unable to find answers to these questions.

1) once i'm in edit mode (after pressing 'i') i noticed that using the keyboard arrows to move will produce a D, B or another letter depending on what arrow i push.
why is that and how can i use the arrows to navigate up, down or left, right?

2) i'm unable to delete a line in edit mode. i try and push the 'delete' key but no go :( how?

3) sometimes when in edit mode, the text i enter does not appear.
any reason why?

i know its a STEEEEEEEEEEEP learning curve for vi and i'm sure i'm doing something fundamentally wrong here so any tips would be greatly appreciated.

ps, i would gladly gedit but am unable to do so when in ssh.

---

### Post by Lars Noodén on 2011-09-29
> **liquidmonkey said:**
> ps, i would gladly gedit but am unable to do so when in ssh.

You can if you tunnel X:
```

ssh **-X** liquidmonkey@some.machine.on.the.net

```

You might also look at Geany or Kate.

---

### Post by dcstar on 2011-09-29
> **liquidmonkey said:**
> 
.........
i know its a STEEEEEEEEEEEP learning curve for vi and i'm sure i'm doing something fundamentally wrong here so any tips would be greatly appreciated.

ps, i would gladly gedit but am unable to do so when in ssh.

vi = **V**irtually **I**mpossible!

Install and use **nano** on the remote machine.

---

### Post by mac4rfree on 2011-09-29
Q1. h,j,k,l are the keys to move around.. ofcourse you need to come out of insert mode and then use it move around.
Q2. Switch to delete mode by pressing Esc and X--> single character, dd -- complete line.

---

### Post by liquidmonkey on 2011-09-29
> **Lars Noodén said:**
> You can if you tunnel X:
```

ssh **-X** liquidmonkey@some.machine.on.the.net

```

You might also look at Geany or Kate.


wow, that little -X has helped out HUGE!!
best tip of the day, thank you!

am also getting better at vi but now i might never need to use it again since i can get gedit up ;)

---

