---
title: "kernels and headers"
date: 2009-12-13
forum: General Help
---

### Post by emanresu on 2009-12-13
i just finished an update which included a kernel upgrade, i guess. during the process, i got a window that asked if i wanted GRUB menu.lst to reflect the new, current or other versions. i stayed with the current. but my menu.lst has kernels going back to 2.6.22 at this point. i'm currently using 2.6.28-11. 
i have two questions:
1) does this mean that there are actually multiple kernels on my computer  or are these just kernel headers in menu.lst that don't refer to anything? 

and 

2) how do i get rid of these old kernels and headers? i tried a little research and someone said to do it through synaptic. i could not find the older kernels in the synaptic list, so i don't know how i'd get rid of them.

---

### Post by Daveth on 2009-12-13
[http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/](http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/)

should sort you out.

---

### Post by Leppie on 2009-12-13
I don't really know grub legacy (I went from lilo to grub2), so I could be wrong about this.
To update your menu.lst if the old kernels aren't on your system anymore you should either edit it manually or run "sudo update-grub". I would opt for the latter after making a backup copy of the file.

---

### Post by emanresu on 2009-12-17
thanks for the suggestions. the first one did not pan out. synaptic has no listings for kernels other than what i am currently running. 

re: the 2nd. i don't mess with GRUB. and i've used sudo vi for manually commenting the kernels from the list of kernels to boot. however, i'd like to remove the kernels completely, not just comment them out of the GRUB list.

---

