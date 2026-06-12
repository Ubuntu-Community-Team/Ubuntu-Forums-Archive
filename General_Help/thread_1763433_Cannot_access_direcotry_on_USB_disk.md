---
title: "Cannot access direcotry on USB disk"
date: 2011-05-20
forum: General Help
---

### Post by lrry on 2011-05-20
There is a little strange behaviour on my usb disk. Today i try to access it and, when i list directory i cannot find one of them.

A result of the command ls -l give me this result for that directory:

<code>
d????????? ? ?    ?        ?                ? directory
</code> 

The disk is formatted in EXT3.

i try chmod and chown, but the system give me a generic I/O error.

The box is a new 1Tb box, ubuntu is 11.04.

Any idea?

Thanks for your response!

---

### Post by dcstar on 2011-05-21
> **lrry said:**
> There is a little strange behaviour on my usb disk. Today i try to access it and, when i list directory i cannot find one of them.

A result of the command ls -l give me this result for that directory:

<code>
d????????? ? ?    ?        ?                ? directory
</code> 

The disk is formatted in EXT3.

i try chmod and chown, but the system give me a generic I/O error.

The box is a new 1Tb box, ubuntu is 11.04.

Any idea?

Thanks for your response!

```
man fsck
```

---

