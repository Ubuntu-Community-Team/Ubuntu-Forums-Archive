---
title: "windows is gone from my bootloader"
date: 2010-01-09
forum: General Help
---

### Post by wcutrombonekid on 2010-01-09
so i turn on my computer today and the windows partition that is normally there is gone, i don't know why or where it went.  the part of the harddrive still exsists because i still have the  282GB partition that i can look at through ubuntu.  but its not on grub.  a little confusing, i don't know what i would have done to make it do that, but any help would be greatly appreciated. also i have another problem.  i have is that for some reason since i upgraded to karmic koala, i have a bunch of old kernals also chilling on grub doing nothing, how do i rid myself of  those?

thanks, chris

EDIT:  wow, windows is not gone from grub, i simply have to scroll down to get to it.

but the other problem still stands because it is the cause of it.

---

### Post by BigCityCat on 2010-01-09
For your lost bootloader.

sudo apt-get install os-prober
sudo os-prober
sudo update-grub2

For your extra kernels. Goto synaptic type in linux headers and completely remove everything that is associated with your old kernels. Be careful. Then

sudo update-grub2

opps unless of course your using an older version then

sudo update-grub

---

### Post by wcutrombonekid on 2010-01-09
sweet, thanks

---

