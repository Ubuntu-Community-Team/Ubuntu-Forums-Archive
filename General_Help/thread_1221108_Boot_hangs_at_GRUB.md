---
title: "Boot hangs at GRUB"
date: 2009-07-23
forum: General Help
---

### Post by nirpius on 2009-07-23
I know this is off topic a little as it occurred using Puppylinux but i know that this issue would be similar on *buntu so I posted it anyway. If it needs moving/removing please tell me.

After my GRUB runs, I get the following terminal screen

```
grub>
```

I have followed many posts about how to get stuff working by trying

```
root (hd
```
```
rootnoverify
```

that kind of thing.

I know my menu.lst thing is located in

sda1/boot/vmlinuz

and it is sda1 that all my loading files are left at.

But whenever i try 

```
rootnoverify (sda1)
```

I get

```
Error 23: Error wile parsing number
```

and if I type

```
setup (hd0)
```

I get

```
Error17:Cannot mount selected partition
```

and if I type

```
setup (sda1)
```

I get

```
Error 23: Error while parsing number
```

~~~

In case it's not blatantly obvious to everyone by now, i don't really know what I'm doing so if you could give me an explanation along with instructions or even better a link to a decent how to then that would be fantastic.

Many thanks in advance :)

---

### Post by SteveDee on 2009-07-24
I don't know if you are running 'buntu & Puppy, or just Puppy, but this may help either way: [http://ubuntuforums.org/showthread.php?t=1203368](http://ubuntuforums.org/showthread.php?t=1203368)

---

