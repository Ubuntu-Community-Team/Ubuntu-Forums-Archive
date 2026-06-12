---
title: "how to view the code in ubuntu"
date: 2009-11-19
forum: General Help
---

### Post by burtab on 2009-11-19
Hello, I´m a ubuntu newbie, so can anyone tell me how do I view the code in ubuntu?
I want to becouse i want modify it.

---

### Post by Giblet5 on 2009-11-19
Sure! The main bits are the kernel (/boot/vmlinuz*). You can download the source via Synaptic. Search for "linux-source".

That's just the kernel. Every program and graphic doodad will have a separate source package. There are ... many of them.

You can also build/install experimental kernel source available from [www.kernel.org](www.kernel.org) (stick to the stable versions).

---

### Post by NoaHall on 2009-11-19
To then view the code from a file, write "cat filename" or "cat filname | less"

---

### Post by Giblet5 on 2009-11-19
> **noahall said:**
> to then view the code from a file, write "cat filename" or "cat filname | less"

+1

---

### Post by Anonymousable on 2009-11-19
-1

cat filename
less filename
gedit filename
:P

But what you want are the sources. To get them, as Giblet said, you'll have to install linux-sources. To modify the actual kernel, you'll have to edit them and then recompile. This takes quite long.

Good luck. :)

---

### Post by fela on 2009-11-19
Ya know guys, the kernel is only the central core of Ubuntu. There are many other components ready for editing.

That said, Ubuntu's kernel consists of alot more than alot of other kernels (e.g. the NT kernel), due to the fact that Linux is monolithic by nature.

---

### Post by John Bean on 2009-11-19
> "cat filname | less"
Give that poster a UUoC Award ;-)

---

### Post by NoaHall on 2009-11-19
> **Anonymousable said:**
> -1

cat filename
less filename
gedit filename
:P

But what you want are the sources. To get them, as Giblet said, you'll have to install linux-sources. To modify the actual kernel, you'll have to edit them and then recompile. This takes quite long.

Good luck. :)

I'd rather do cat filename | less . It's cleaner.

---

### Post by Giblet5 on 2009-11-19
Hey now... The NT kernel was *supposed* to be monolithic. At least, according to the VMS guy that wrote it...add 1 to the letters VMS and what do you get? That is not a coincidence. Use that when a 'doze fanboy calls Linux an "old" OS; Windows NT is far older (and inbred).

@Anonymousable: 'cat file.c | less' will work just fine. You're just coming down from the caffeine buzz.

For better justice: ```
kate *.c
```

Tabbed, sorted, syntactically highlighted, with collapsible function definitions. What's not to like.

Almost as good as ```
vi `find . \( -name \*.c -o -name \*.s \) -print`
```

---

