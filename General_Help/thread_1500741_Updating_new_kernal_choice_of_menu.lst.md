---
title: "Updating new kernal choice of menu.lst"
date: 2010-06-03
forum: General Help
---

### Post by Benchrest on 2010-06-03
I have solved my problem but I don't think I did it the right way. That is the answer I am looking for.

This morning I had 10 updates for my system including a new kernel 2.6.28-19  During install I was asked a question as to which menu.lst to use. I was completely confused as there was no documentation explaining the choices, so I took the default, keep my current menu.list. I did that because I have a modification to my menu.lst having added acpi-noirq  I was afraid I would loose that and not be able to boot. Anyhow I ended up with my same menu.lst without the new kernel. So it booted the old kernel 2.6.28-18   Where is some documentation to give one some idea of which of the about 8 choices to make? I can't be the first with this problem. I have another computer to undate that has a different mod to menu list.  I would like to know the correct way to choose the proper choice. If I don't get an answer I will try to document in more detail the choices.

I got around the problem by editing menu.list and copying the entries for 2.6.28-18 and changing them to 2.6.28-19 Many folks might not even realise they were running on the old kernel.

---

### Post by oldos2er on 2010-06-03
[https://wiki.ubuntu.com/KarmicKoala/ReleaseNotes#GRUB%20menu.lst:%20install%20the%20maintainer%27s%20version%20vs.%20keep%20the%20local%20version](https://wiki.ubuntu.com/KarmicKoala/ReleaseNotes#GRUB%20menu.lst:%20install%20the%20maintainer%27s%20version%20vs.%20keep%20the%20local%20version)

---

### Post by Benchrest on 2010-06-05
Thanks for your reply.  I find it a little difficult to understand but I think I figured it out. At first I thought this is still a poor solution as a person has to read through the menu.lst in the middle of installing an update to understand what to do. But this only occurs if one has modified menu.lst so maybe they will get a solution some how even if it is like I did. Still not sure anyone should have to mess with menu.lst. What does a new person do? Marking solved until I hit the problem again.

---

