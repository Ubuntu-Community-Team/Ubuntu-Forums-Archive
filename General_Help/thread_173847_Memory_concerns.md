---
title: "Memory concerns"
date: 2006-05-11
forum: General Help
---

### Post by kentshultz on 2006-05-11
Hi all.

I am a relatively new Ubuntu user and I have noticed that my system appears to be consuming an inordinate amount of memory.  I have 1gb of memory and on a fresh reboot the system is consuming a little less than half of that memory, but after a few hours of light use (web browsing, email, IM, music, etc), top reports about 900mb of memory is being used.  The hungriest processes are Xorg (155mb) firefox (89mb :( ), gaim (26mb) and the rest down from there don't consume much memory.

Is there something I am missing here?  I was under the impression linux shouldn't be this memory hungry.

I am running Breezy with GNOME.

Thanks guys.

---

### Post by Dr. Nick on 2006-05-11
I think linux measures memory usage in another way. Im using 881 of 1 gig but its still very responsive. I think people have described why it appears so much memory is being used, buti forgot exactly

Edit
[http://gentoo-wiki.com/FAQ_Linux_Memory_Management]("http://gentoo-wiki.com/FAQ_Linux_Memory_Management") 
this was linked from another thread [here]("http://ubuntuforums.org/showthread.php?t=172645&highlight=memory+usage") detaiing the numbers

---

### Post by loell on 2006-05-11
I ran breezy with 256mb of memory, and it still is responsive..
:)

---

### Post by kentshultz on 2006-05-11
[QUOTE=Dr. Nick]I think linux measures memory usage in another way. Im using 881 of 1 gig but its still very responsive. I think people have described why it appears so much memory is being used, buti forgot exactly

Edit
[http://gentoo-wiki.com/FAQ_Linux_Memory_Management]("http://gentoo-wiki.com/FAQ_Linux_Memory_Management") 
this was linked from another thread [here]("http://ubuntuforums.org/showthread.php?t=172645&highlight=memory+usage") detaiing the numbers[/QUOTE]

heh, that clears things up.... sort of.

Well at least I know its normal behavior anyway :)

---

### Post by Dr. Nick on 2006-05-11
[quote=loell]I ran breezy with 256mb of memory, and it still is responsive..
:)[/quote] 
Heh I had 128 at one time in my laptop, It was responsive enough to use aswell lol.

Basically I think linux uses all the memory it can for one thing or another just so its not wasted. People always tend to assosciate a lot of free memory with speed, when that is not always the entire case. What is the point of 1gig or ram if you use 400 of it, might aswell just have 512? I would rather use 900 of it and lessen the load on the hard drive.

---

### Post by nanotube on 2006-05-11
still, that gentoo article was useful. i set my swappiness to 30 (from the default 60), because there is a lot of cache, but also a lot of swap being used on my laptop. so i figured, i will see how it works if i make it less swap-happy. don't know if it will make a difference, will post back and let y'all know. :)

---

