---
title: "Kill Copy File Command"
date: 2011-06-06
forum: General Help
---

### Post by Priswell on 2011-06-06
I started to copy a directory using Nautilus. I dragged and dropped a directory from my hosted server to my home drive. It got hung up, and wouldn't download. I clicked the red "stop operation" button, but I have a lingering icon in my upper panel saying that I still have file operations going on, even though it has supposedly stopped. How do I determine from the command line what this process is named and how do I kill it to remove the icon?

Ubuntu 10.04 64 bit

---

### Post by raja.genupula on 2011-06-06
right click at your panel
--> add to panel
new window going to open 
select the force quit application 
add it to the panel
,

then click at that added force quit icon in your panel. then click t at hat process window. that process will be quit.

---

### Post by sbraz on 2011-06-06
i'm not sure but when i copy stuff around **top** shows that nautilus uses some cpu, so i'd try something like **pkill nautilus**, which would kill all nautilus's child processes.

i've tested it now and it works. no idea about hung processes though.

---

### Post by Priswell on 2011-06-06
I was unable to find anything I recognized as "nautilus", but running **pkill nautilus** worked. Thank you very much.

Using the method of the "force a misbehaving application to quit" by setting up the applet in the panel did not work, but I appreciate the mention of it.

---

### Post by sbraz on 2011-06-06
nice!

i've just re-read your post and i presume that clicking the red X to stop copying and then simply unmounting the remote volume by pressing the eject button in nautilus should work too, as it worked here at home while copying files to my often overheating-then-crashing-while-i-need-it backup pc. :D

---

