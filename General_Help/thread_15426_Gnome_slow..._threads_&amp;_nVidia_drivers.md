---
title: "Gnome slow... threads &amp; nVidia drivers"
date: 2005-02-14
forum: General Help
---

### Post by jarav on 2005-02-14
Hi everybody,

is it okay that just moving the window (especially when its over another window) can eat up to 100% of CPU resources? It seems that a lot of linux users have problems with graphics responsiveness and I want to know if there's actual problem or it's "just the way it is" in linux...

btw I was trying to do something with it today and found a czech guide to installing nVidia drivers, where they say you should comment/delete the Load "dri" and Load "GLcore" lines in XF86Config-4. There's no such thing in [www.ubuntuguide.org](www.ubuntuguide.org) though... 

There SEEMS to be improvement in overall "feel" (noticeable when displaying menus, etc.) so you might just want to try it   :) . But the problem with CPU load when moving windows still persists...

So, is there someone who could confirm, that CPU load during moving windows is or isn't normal and if commenting those two lines can actually improve performance of nVidia cards?

My system is Athlon-Thunderbird 950, 512 MB RAM running Warty with K7 kernel...

Thanks in advance

J.

---

### Post by scoon on 2005-02-14
Hey there, 

go here: [http://www.nvidia.com/object/linux_display_ia32_1.0-6629.html](http://www.nvidia.com/object/linux_display_ia32_1.0-6629.html)

Download the README.txt file and read it!!!!  By then end of it, you will be the nvidia master.  (Just like everyone else that has read that file).

scoon

---

### Post by jarav on 2005-02-15
Okay, thanks, it's strange, but i still don't feel like expert though. 

They say you should comment theese lines, but not why and if it does have effect on performance or not. And why it isn't in ubuntuguide.org? And is it normal in linux that moving window eats up CPU time? Or not?

---

### Post by scoon on 2005-02-15
Hey there, 

It is not a normal thing.  Something is not happy. 


scoon

---

