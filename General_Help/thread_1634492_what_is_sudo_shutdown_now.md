---
title: "what is sudo shutdown now"
date: 2010-11-30
forum: General Help
---

### Post by c2tarun on 2010-11-30
hi friends
can anyone tell me the difference between 
"sudo shutdown now" and "sudo shutdown 0"

i know that "sudo shutdown 0" will shutdown the system in 0 seconds.
but when i run sudo shutdown now my system goes into the maintenance mode???
what is maintenance mode??

---

### Post by sikander3786 on 2010-11-30
It shouldn't go to maintenance mode anyways. Do you mean recovery mode? That is selected via Grub menu, shutdown command shouldn't effect that anyway.

See man pages for more details.

```
man shutdown
```

I like adding -h parameter which halts it.

```
sudo shutdown -h now
```

---

### Post by I'mGeorge on 2010-11-30
> **c2tarun said:**
> hi friends
can anyone tell me the difference between 
"sudo shutdown now" and "sudo shutdown 0"

i know that "sudo shutdown 0" will shutdown the system in 0 seconds.
but when i run sudo shutdown now my system goes into the maintenance mode???
what is maintenance mode??

I don't know what do you mean by maintenance mode but those commands should have the same effect. 0 it's as you already suggested 0 sec or no time at all while now does the exact same thing as one of the command's parameters.

---

