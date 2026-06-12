---
title: "Ok, so hmm..."
date: 2006-04-26
forum: General Help
---

### Post by sinkxdie on 2006-04-26
In my Grub Menu I have 4 different Ubuntu Os's...well at least I don't think I do
There is the word Ubuntu, then a couple words and numbers, and then a date in parenthethees.[()]
I think this might be why I went from 2gb to 200mb in 2 days. And also, all these *Os's* go to the same OS, my Ubuntu.
I also recently installed/upgraded to Dapper, so mabey this is the cause of this?:cry:

---

### Post by dermotti on 2006-04-26
There are your old kernel's. Generally the newest one is the first kernel in your list.

You can safely remove the old kernels via synaptic.

---

### Post by xXx 0wn3d xXx on 2006-04-26
[QUOTE=sinkxdie]In my Grub Menu I have 4 different Ubuntu Os's...well at least I don't think I do
There is the word Ubuntu, then a couple words and numbers, and then a date in parenthethees.[()]
I think this might be why I went from 2gb to 200mb in 2 days. And also, all these *Os's* go to the same OS, my Ubuntu.
I also recently installed/upgraded to Dapper, so mabey this is the cause of this?:cry:[/QUOTE]
Those are different kernels. They all point to the same operating system but different linux kernels.

---

### Post by sinkxdie on 2006-04-26
Dermotti said to uninstall using Synaptic, but what would I uninstall?

---

### Post by xXx 0wn3d xXx on 2006-04-26
[QUOTE=sinkxdie]Dermotti said to uninstall using Synaptic, but what would I uninstall?[/QUOTE]
In terminal type:
> 
uname -r

that will give you your current kernel version. Then you can search for "kernel image" in synaptic and remove the old kernels. DON'T remove your current kernel.

---

### Post by jobezone on 2006-04-26
using synaptic, search for "linux-image" and you'll get a list of many linux-image-* packages, with a few of them installed (with a green box behind them). Remove the ones that you don't want to have (those extra ones in the GRUB menu). Remember that even if you only have one linux installed, the GRUB menu usually shows 3 options for booting it.

---

### Post by sinkxdie on 2006-04-26
Yeah, I got it. I rebooted, and wrote down the old kernels. :D
Yay, I freed 300mb!

---

