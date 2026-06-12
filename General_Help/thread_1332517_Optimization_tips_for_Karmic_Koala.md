---
title: "Optimization tips for Karmic Koala?"
date: 2009-11-20
forum: General Help
---

### Post by GetOutOfBox on 2009-11-20
I'm sort of new to linux, but I am familiar with the essential commands, and I pick up new ones fast.

Anyways, I'm just looking for any performance optimization tips, be it small to large scale kernel changes. And as you can see from the title, they have to be compatible (or have an effect) with Ubuntu 9.10.

P.S, You don't have to explain each trick in the post, you can just post a link, or even just the term related to the optimization. And be specific, don't just say "Optimize Your Kernel", post specifically what to optimize in the kernel, etc.

Don't worry about dumbing things down for me, I'll just use google if I don't understand something.

---

### Post by kerry_s on 2009-11-20
try the other "elevator" options. you just add it to /etc/default/grub & run update-grub. cfq is the default, but it's not always the best, different hardware gives different performance feeling.

read here:
[http://www.redhat.com/magazine/008jun05/features/schedulers/](http://www.redhat.com/magazine/008jun05/features/schedulers/)

i've dropped down to jaunty, so can't look to give you detailed in instructions. i use "elevator=as" on mine, i get less disk activity, so it feels faster, i'm running an atom 1.6 with 512mb ram.

if you have a fast machine i recommend you try the "elevator=deadline" which is suppose to be like more real time performance.

make sure you do the /etc/hosts file fix, it really does help the responsiveness feeling.

that's pretty much all i do now a days, other then the software side, where i use lighter programs instead of the heavier stuff.
example: 
abiword instead of open office.
gpaint instead of gimp.
leafpad instead of gedit.
etc...

forgot, i also do the gnome performance:
[http://library.gnome.org/admin/system-admin-guide/stable/performance-0.html.en](http://library.gnome.org/admin/system-admin-guide/stable/performance-0.html.en)

---

