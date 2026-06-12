---
title: "Woohoo! - Success at last with full system restore"
date: 2009-08-21
forum: General Help
---

### Post by tgeer43 on 2009-08-21
First of all, to those who tried helping me to restore my system from backup after a crash - thanks for your efforts.

It turns out that all of the bizarre errors I was getting which made absolutely no sense were actually related to a failing drive. No wonder I/we couldn't figure things out. I was pissing in the wind the whole time. Too bad I spent over a week of sleepless nights banging my head against the wall. :(

Anyway, I ended up replacing the failing 100GB 2-1/2" SATA notebook drive with a shiny new 320GB unit (only $89 on sale at a local retail outlet - not too bad). I partitioned, formatted and extracted the backup tarball to it. Then I installed  and configured grub but for some reason could never get update-grub to complete successfully. So I edited menu.lst and fstab manually to reflect the drive's new UUID and voila! - it booted right up and my system was right back to the way it was before this whole fiasco. I had spent countless hours configuring and tweaking this 9.04 64-Bit installation and *really* didn't feel like starting over from scratch. I am *very* happy. :D

Besides getting a new high-capacity drive, there was another upside to this. I learned a *LOT* about the internal workings of the operating system that I probably would never have otherwise had a chance to experience. As a result I'm much more confident that I can recover from future disasters should they occur.

Thanks for reading,

tgeer

---

### Post by enli on 2009-08-21
I couldn't agree more on the fact that we learn things that we actual experience in real life. May it be maths/science concept when linked to some real life object/idea helps to learn and remember effectively.

Glad to hear that you sorted problem yourself. There is nothing more joyful when you figure out things yourself :D

---

