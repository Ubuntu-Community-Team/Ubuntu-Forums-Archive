---
title: "confusion in /etc/default/grub"
date: 2011-12-14
forum: General Help
---

### Post by pmx on 2011-12-14
Hi,

In the file, /etc/default/grub,

there is a line:

GRUB_HIDDEN_TIMEOUT=0

and since I want to display the menu (while PC boots), I should make this line as:

```
GRUB_HIDDEN_TIMEOUT=
```
or
```
#GRUB_HIDDEN_TIMEOUT=
```

Doing anyone of the above two is same?

---

### Post by Iowan on 2011-12-14
My 11.10 laptop has ```
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
```

*/etc/default/grub* also had an interesting note about:> #  For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

---

### Post by pmx on 2011-12-15
Is

```
#   info -f grub -n 'Simple configuration' 			 		
```

a file or command?

---

### Post by matt_symes on 2011-12-15
Hi

Anything with a # in front of a line is a comment. This is used to convey information to you, the reader.

If there is no # then it is an instruction for the computer.
```

sudo update-grub
# this line is a comment. The above line is an instruction.
```

Kind regards

---

### Post by pmx on 2011-12-15
oh ok, thanks man.

---

