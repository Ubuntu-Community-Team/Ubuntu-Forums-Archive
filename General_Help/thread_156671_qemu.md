---
title: "qemu"
date: 2006-04-07
forum: General Help
---

### Post by PriceChild on 2006-04-07
Hey, i'm really wanting to get rid of windows atm, but thought it'd be nice to use a virtual machine occasionally. Read a post on here which suggested qemu was definately the way to go and i've installed it via synaptic.  I've seen something about kqemu though... is this needed? Can i install it even though i've installed qemu or do i need to compile it?  Really should compile my first app soon, been putting it off :P  Any help would be greatly appreciated, Thanks, Pricey

---

### Post by Azrael on 2006-04-07
[quote=PriceChild]I've seen something about kqemu though... is this needed?[/quote] Kqemu is not needed, but it will make the guest OS run a lot faster. Unless you have very fast hardware, qemu without kqemu (or the other open source alternative accelerator (forgot the name)) runs painfully slow...

This howto is the one I originally used to get things working: [http://ubuntuforums.org/showthread.php?t=39513]("http://ubuntuforums.org/showthread.php?t=39513")
(check the posts in the last page of the thread for an easy script)

For more (uptodate) info and instructions, check the qemu website:
[http://fabrice.bellard.free.fr/qemu/]("http://fabrice.bellard.free.fr/qemu/")

---

### Post by ayates on 2006-04-07
Check this thread:

[http://ubuntuforums.org/showthread.php?t=84275&highlight=vmplayer](http://ubuntuforums.org/showthread.php?t=84275&highlight=vmplayer)

---

### Post by PriceChild on 2006-04-07
what's the downside to vmplayer? i can't seem to understand its limitations

There must be one :S

I have win98 working fine in qemu atm (temporarily lost my xp cds somewhere)

---

### Post by ayates on 2006-04-07
I used Qemu(with Kqemu) for a while and it was very slow. Vmplayer is so much faster. No downside for me.

---

