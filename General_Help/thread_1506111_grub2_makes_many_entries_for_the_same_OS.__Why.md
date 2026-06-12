---
title: "grub2 makes many entries for the same OS.  Why??"
date: 2010-06-10
forum: General Help
---

### Post by quixote on 2010-06-10
For some reason my grub is giving me six (6!) repetitions of my Ubuntu Lucid install on sda5, five repetitions of my old karmic install on sda1, and I think four of the recovery option.  Where have I told it to do that?  How do I fix it??

The grub choices look like this:```

most recent lucid kernel on sda5                    
most recent lucid kernel recovery option     
last lucid kernel on sda5                           
last lucid kernel recovery option    
    *(now the fun starts:)*
six entries which point to the same Lucid as the first one above,
 slightly different title, but same sda5

some duplicate recovery entries

five duplicates of karmic on sda1

```

I've edited /etc/grub.d/40_custom, but all the changes I made are now commented with a # and presumably nonfunctional?  The only real lines are at the beginning: ```
#!/bin/sh
exec tail -n +3 $0
```  Possibly I also edited 10_linux, but if so I can't find where. 
:oops: and  :confused:

---

### Post by LiquidMeson on 2010-06-10
if you want to edit grub the best way now is to sudo nano /etc/default/grub
followed by a sudo update-grub

if the extra kernels still show up and sudo apt-get autoremove doesn't get rid of them feel free to head into /boot and delete the extra kernels..(remove the files with old numbers)

again: proceed with update-grub

think of it like old snake skins. in-case you get nostalgic you can go back.

---

### Post by garvinrick4 on 2010-06-10
They are all the same kernel? Is that what you are saying. What is in your synaptics
in GUI? Can delete kernels from there. Most likely all different kernels. Just type in
search 2.6.32-xx or whatever the kernel you do not want and its headers.
 What does this code say:

```
sudo aptitude update && sudo aptitude upgrade

```
Does it give you a lot of packages to be deleted?

---

### Post by quixote on 2010-06-10
That's exactly it: they're duplicates of the same kernel!  I went through and deleted obsolete kernels a while ago.

Yes, the system offered to delete a list of obsolete packages when I upgraded to lucid.  There was one in the list I actually needed, but when I went to select that one, it just assumed I wanted to keep all of them.  I haven't worried about it, but you think it could be causing this issue?  ??  I guess I don't see how, but I'll try what you suggested.

---

### Post by garvinrick4 on 2010-06-10
> **quixote said:**
> That's exactly it: they're duplicates of the same kernel!  I went through and deleted obsolete kernels a while ago.

Yes, the system offered to delete a list of obsolete packages when I upgraded to lucid.  There was one in the list I actually needed, but when I went to select that one, it just assumed I wanted to keep all of them.  I haven't worried about it, but you think it could be causing this issue?  ??  I guess I don't see how, but I'll try what you suggested.
Even it you:

```
sudo update-grub
```
```

sudo grub-mkconfig
```


It leaves duplicate kernels in grub menu?

---

### Post by quixote on 2010-06-15
Okay, this is really embarrassing.  The string of what I thought were duplicate kernels were on another partition than the one I thought.  Once I finally realized that, looked at the right partition, there was a whole series of kernels that needed deleting.  I was so convinced I'd dealt with that long ago, I wasn't reading the kernel list carefully enough.  I *thought* I was.  Honest!  Once I got rid of them and updated grub: end of problem. So grub was working fine all along.

:redface: :redface: :redface: . . .  #-o

Thanks to all for your help, and making me read what was right in front of my nose!

---

