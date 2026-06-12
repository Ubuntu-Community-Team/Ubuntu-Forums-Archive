---
title: "data at shutdown"
date: 2010-11-13
forum: General Help
---

### Post by b3rylord on 2010-11-13
When I shutdown the PC there is a page of data itemising actions taken, but it is there and gone before I get the chance to read it. Is there any way to preserve this to a txt file to read at the next power up?

Ubuntu 10.10

---

### Post by nlsthzn on 2010-11-13
I suspect all you are seeing is the OS unmounting the file system, killing any required applications and going through the different run levels until it reached the point it shuts down or reboots... It isn't important... not sure of a way to interupt it so you can see... maybe go into a console via Ctrl+Alt+F3... then type reboot --help and see if there is an option to make it wait... then run reboot with that option, you should then be able to see all of the text before reboot...
 
(If I wasn't in Windows at work now I would try it myself)...

---

### Post by b3rylord on 2010-11-13
Thanks for that, it worked for as long as it took for me to satisfy my curiosity as to what was going on, and it was a distinctly more orderly shutdown than Windoze, and much much faster.......

---

