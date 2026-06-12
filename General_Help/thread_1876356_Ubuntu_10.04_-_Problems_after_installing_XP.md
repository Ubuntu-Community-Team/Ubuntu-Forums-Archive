---
title: "Ubuntu 10.04 - Problems after installing XP"
date: 2011-11-06
forum: General Help
---

### Post by ubuntdos on 2011-11-06
Hello everyone, I’ve been using Ubuntu 10.04 for a little while now but I needed to reinstall windows xp. So Ubuntu disappeared from the startup and I used that boot fixer to get GRUB up and running again. Problem is Ubuntu doesn’t work anymore for some reason…I have some very important files on there and if I could only figure out how to at least copy them on a usb drive I’d be happy. 

When I choose generic ubuntu it brings me to the loading screen, all I get is the Ubuntu logo and it freezes… Nothing happens, that little progress animation doesn’t even appear. So first I restarted the computer and tried to run memtest86+. Nothing popped up. Then I tried going into recovery mode, first off I tried to repair broken packages, and I updated the grub bootloader and when I restarted the computer the same error happened. The logo appeared but then froze. 

So then I tried using the failsafeX mode in the recovery menu. I get this prompt, “Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself.” No matter what option I choose, or path of options I follow I end up with a black screen. And now that I’ve resested  a few times it’s become even more uncooperable. It’s getting harder and harder to even reach the recovery menu when I choose recovery mode. It’s starting to freeze even when it’s loading that. (Windows is still working perfectly btw). 

Is there anyway of reparing Ubuntu without having to clean install it? i.e. preserving all my files.  

How do I recover my files?

Also, I DID manage to reach root command in the very beginning but I’m a purely GUI user so I had no clue what to do once I got logged in. If on the off chance that I do get there again is there a guide on how to operate Ubuntu from the command line? What I want to do is first see what’s on my desktop, browse through files, locate the important files I’ve been looking for and transfer them onto my usb stick.

Thanks

---

### Post by cllewis91592 on 2011-11-06
well last time i had a system crash i used a live cd to boot into a temporary user state kinda thing. there you can view your files and copy them somewhere else. 

i have heard that if you have ubuntu installed first and then install windows over it they dont really get along. its better to have windows first then put on ubuntu(if you plan to reinstall)

---

### Post by ubuntdos on 2011-11-06
Hey cllewis I'll try that but my live CD is Ubuntu 8.04, you think I should make a new live CD? Unfortunately for me I don't have /home on a seperate partition either so I can't just reinstall it.

ETA: **** ME IT WORKED. I could kiss you cllewis.

---

### Post by cllewis91592 on 2011-11-06
> **ubuntdos said:**
> Hey cllewis I'll try that but my live CD is Ubuntu 8.04, you think I should make a new live CD? Unfortunately for me I don't have /home on a seperate partition either so I can't just reinstall it.
im sure as long as you have a live cd you should be able to do a live boot. just select "try ubuntu before installing" or something along those lines. that should let you explore your hard drive and copy things. trust me ive had to do this many a time (lots of stupid mistakes on my part :lolflag: but we learn from our mistakes right?)

---

### Post by ubuntdos on 2011-11-06
> **cllewis91592 said:**
> im sure as long as you have a live cd you should be able to do a live boot. just select "try ubuntu before installing" or something along those lines. that should let you explore your hard drive and copy things. trust me ive had to do this many a time (lots of stupid mistakes on my part :lolflag: but we learn from our mistakes right?)

Thank you! Saved my life :)

Next time: Install home in a seperate partition, backup, install windows before, and use the terminal more often.

---

