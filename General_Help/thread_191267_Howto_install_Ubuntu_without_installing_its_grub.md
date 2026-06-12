---
title: "Howto install Ubuntu without installing its grub?"
date: 2006-06-07
forum: General Help
---

### Post by funkyou on 2006-06-07
Hello there,

I have a small question... How do I install dapper without installing its grub?
I have just downloaded the alternate install cd and want to install it on a second hdd, but i have another distribution which is my main os and so i dont want to install dappers grub but use the one from my other distribution...

So, how can i do this? I just want to manage my grub menu not from dapper, but include it into the grub of my other linux installation...

Btw: I have no fdd, so i can not install grub to a floppy disk...

The other question is: When i install dapper from the alternate install cd, does it write a grub mbr automatically? This would not be so good...


Thx

---

### Post by xtacocorex on 2006-06-07
You might have to use the Alternate (text-based) install cd and use the expert mode so you can skip over installing grub.

At least it's an idea, haven't tried it for this particular action though, but I have done that method to reinstall grub after screwing stuff up on my Breezy system.

---

### Post by mcduck on 2006-06-08
Alternate disk won't automaticly install Grub. It'll ask you if you want to install it. Just say no, and you'll get into the expert mode (for a while) that allos you to install LILO instead. Jump over that step too, and the installer will continue in the normal way without installing a bootloader.

---

