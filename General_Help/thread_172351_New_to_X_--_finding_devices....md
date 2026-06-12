---
title: "New to X -- finding devices..."
date: 2006-05-08
forum: General Help
---

### Post by cheuschober on 2006-05-08
Hi-

I've been seriously working with linux for about 4 months now and have found myself needing to branch out into some of my more laptop power-user-esque machine uses.

Today, before a presentation later in the week, I'm going to try to get my laptop vga-out working. Now the end result, of course, is that I'll be able to write a little bash script that'll be able to switch me, on-the-fly, from single-screen desktop to a shared desktop environment where display1 gets desktop1 and display2 gets desktop2 with some auto-detect thrown in there for cold-boots. But, lets' start small.

The laptop in question is your standard el-cheapo Toshiba Satellites from a couple years ago (A145-S130 I believe) with the previous generation intel integrated video (855GM) a dusty attached 15" lcd, a vga-out port in the back, and an innocuous samsung 17" lcd sitting next-door.

My rather generalized conversation stems from pouring through the various wiki's and how-tos on the subject. I have a basic understanding of how to define the necessary display devices and desktop devices and how to close / restart X to bring the new settings back in. What I'm lacking in, then, is a much more general problem for me in all respects (running into it with USB, pointers, keyboards, etc etc): 1) finding my devices and 2) knowing how to configure them properly.

Now, I recognize that there's a good chance that I've probably just missed that how-to but thus far I can't tell how to locate my various devices, in this case the internal and external display ports. After I locate them, then, I'm going to have to 'configure' them in xorg.conf and pass all the necessary pieces of information such as type, driver, etc. Some bits, like resolution, are easy -- others, like driver ... well, where's our driver list to pick from? I'd hate to just spend the next 5 years generating combinations of "Intel 855GM Display Driver" ... "intel 855gm display driver" ... "Intel 855(GM) Display Driver" and so on and so forth -- you get the idea. Is there a database somewhere I've missed that notes the driver name meant to be associated with which pieces of hardware?

I've no doubt that it'll all work -- if I cold-boot with vga plugged in it takes my vga-out as the primary (and consequently only) monitor -- I'm simplly in need of a little more education on the philosophy of and tools for execution than in the actual execution itself.

As always any and all help is appreciated.

~Chad

---

