---
title: "Broken Sudoer and Encrypted Drive"
date: 2012-05-01
forum: General Help
---

### Post by BryanPotts on 2012-05-01
So, last night in the wee hours of the morn', I had enough hubris in me to modify the sudoers file without using visudoers.

This is the point where everyone points and laughs, as they know I put in a syntax error.

That's an easy problem to solve with a LiveCD. However, the drive is encrypted, and we don't have the key.

I've gone as far as to try to run

```
cat /root/*
```

```
dd if=/dev/sda1 | ssh user@foreign.computer "dd of=/some_location"
```

and even

```
dd if=/dev/"Swap_Partition" | ssh user@foreign.computer "dd of=/some_location"
```

Which obviously didn't work, as both the main and swap partitons are encrypted.

Thankfully it's a fresh install of Ubuntu Server, so I don't mind wiping it. 

But my morbid curiosity begs me to ask if there is ANY way to retrieve the key.

---

