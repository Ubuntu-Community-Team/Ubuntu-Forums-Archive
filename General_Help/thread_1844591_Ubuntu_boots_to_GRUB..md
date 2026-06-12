---
title: "Ubuntu boots to GRUB."
date: 2011-09-15
forum: General Help
---

### Post by YayOpenSource on 2011-09-15
My ubuntu (natty) has suddenly stopped working and instead is going straight to this screen
> 
[CENTER]GNU Grub version 1.99~rc1-13ubuntu3[/CENTER]

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

grub>

I have Ubuntu installed on wubi and can access windows with no problem, help please :( Many thanks in advance.

---

### Post by Synoc on 2011-09-15
before we can help, some clarification would be helpful. you said it suddenly stopped working, did it work before and, if so, what did you do before it stopped working correctly?

---

### Post by drs305 on 2011-09-15
Take a look at the Wubi Megathread:
[http://ubuntuforums.org/showthread.php?t=1639198]("http://ubuntuforums.org/showthread.php?t=1639198")

See if Problem #2 relates to your situation. Solutions are presented to various WUBI boot problems.

---

### Post by YayOpenSource on 2011-09-15
Ubuntu was working correctly yes but the netbook I have it installed on (Acer Aspire One) has a major motherboard flaw in that it regularly hangs completely which means everytime it has done that in Ubuntu I've had to pull the battery out and whatnot, so I don't know if the unclean shutdowns are a factor in it dying or not.

---

### Post by bcbc on 2011-09-15
Try this for finding the root.disk (which is likely the problem): [http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html)

Also try to avoid taking out the battery. Try these options first: [https://wiki.ubuntu.com/WubiGuide#How_to_reboot_cleanly_even_when_the_keyboard.2BAC8-mouse_are_frozen](https://wiki.ubuntu.com/WubiGuide#How_to_reboot_cleanly_even_when_the_keyboard.2BAC8-mouse_are_frozen)

Or better yet try to figure out if there is a kernel boot option that will prevent it from hanging. What's the model number and graphics card?

---

