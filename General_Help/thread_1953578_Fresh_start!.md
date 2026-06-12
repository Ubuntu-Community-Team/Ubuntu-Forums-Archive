---
title: "Fresh start!"
date: 2012-04-06
forum: General Help
---

### Post by benj23673 on 2012-04-06
So after messing with my unity launcher and not being able to log into my "main" account I decided to start fresh again! considering I only started running ubuntu about a week ago. I am still trying to learn but here is my question (I am dual booting ubuntu next to windows on the same hard drive) I want to just start fresh whats the best way? do I delete the ubuntu partition via windows? is there some better way? Some one please crack an egg of knowledge on me

---

### Post by TeoBigusGeekus on 2012-04-06
Just fire up an ubuntu live cd/usb and install it over your previous installation.

---

### Post by benj23673 on 2012-04-06
I tried that but when it gives you the three options install next to operating systems, erase everything, or do it manually what one do I pick? manually? and if so how do I go about doing that? I'm too new to this stuff

---

### Post by PhantomTurtle on 2012-04-06
It depends on how you want to go at this. If you wanted Grub NOT to overwrite the Windows MBR, then your going to have to partition it yourself. IF you don't want to do this, then delete the Ubuntu partition in Windows and install over the free space.

---

### Post by benj23673 on 2012-04-06
I don't know if I want grub to overwrite the MBR (from what I understand of a MBR after my quick wiki search) I don't think it really matters that much I guess?

---

### Post by Monotoko on 2012-04-06
What TeoBigusGeekus suggested would work if Ubuntu was the only system on there, if you have Windows on there as well it becomes a little more complex. The MBR also won't matter, as the Ubuntu installer will update GRUB when it is done. 

What you need to do is go for "Manual", find your old Ubuntu partition, right click, choose change then specify Use As to ext3/4 (which ever you like) then mount point to "/" and check the format button.

This will essentially reuse your old partition, without making you have to do any new partitioning.

---

### Post by PhantomTurtle on 2012-04-06
If you do not mind then delete your current Ubuntu partition in Windows and then install over the free space with the Ubuntu Live cd/usb.

---

### Post by benj23673 on 2012-04-06
I am going to look into both options thank you guys very much if doing it from live disk gets a little to out of hand for me I may just delete the partition via windows either way thanks for the knowledge.

---

