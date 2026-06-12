---
title: "New kernel problem, seems easy to solve but im lost!"
date: 2009-09-29
forum: General Help
---

### Post by jessiebrownjr on 2009-09-29
I followed the master kernel thread, did everything...  now when I finished up the last step, i rebooted... There wasn't a grub entry for the new kernel..

Now a couple of variables..  I have backtrack 4 installed...

The way it was installed was... semi weird..
I installed off a fresh HDD, put on ubuntu, then vista.
the swap file I made was WAY too large, and knowing this, I cut it down to 6GB and put a 7gB partion as an ext3 filesystem for backtrack...

I previously hand edited the menu.lst file while I was on my Ubuntu install, and the changes didn't effect the grub I was seeing..  So i remembered it got "super ugly " after I installed backtrack 4, so I booted into it, and edited the menu.lst there.. THAT changed the grub I saw when I booted.. (if you can explain this to me as well Id love that :-) )

Ok, so I ran update-grub on the Ubuntu install AFTER i rebooted the first time, saw nothing...

So then I went into backtrack 4, ran upgrade-grub, it gave me a new type of box that said etc versions were found, what do you want to do? I chose "install new"

Rebooted... saw nothing..

Now im just baffled.

if I run "computer janitor" in system > admin, I see the 2 files I have just created as 'trash' now..

Thats why I think I did 99% of it right, but it didn't install it properly maybe?

Im lost as to what to do now, please help! thanks guys!

---

