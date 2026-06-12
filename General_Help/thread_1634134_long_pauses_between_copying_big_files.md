---
title: "long pauses between copying big files"
date: 2010-11-30
forum: General Help
---

### Post by c2tarun on 2010-11-30
hi friends
when i try to copy more than one files of average size of around 300MB, ubuntu copy one file then data transfer stops for some time, and then after it continues and again stops on the end of file??
i didnot faced this problem while copying data to my external hard drive.
why so??

---

### Post by a-user on 2010-11-30
are you copying to an external drive? i it attached with usb2. when you say "ubuntu makes a break" could it be that your external drive still i working? in that case the file has not finished to copy. the external drive is slower than your internal. the data gets buffered. reading from internal has finished but not writing. thus it first empties the buffer before continues with the next one.

---

### Post by c2tarun on 2010-11-30
> **a-user said:**
> are you copying to an external drive? i it attached with usb2. when you say "ubuntu makes a break" could it be that your external drive still i working? in that case the file has not finished to copy. the external drive is slower than your internal. the data gets buffered. reading from internal has finished but not writing. thus it first empties the buffer before continues with the next one.


yeah i was copying file to usb pendrive.
may be it is bit slower?? but in the last file it shows 0 seconds remaining and then waits for 2-3 minutes before file operation pop up disappears.

---

### Post by a-user on 2010-11-30
it is like i explained. it shows 0s remaining cause the operation of copying has finsihed BUT not all data has flushed to the pendrive. there are still some bytes left in the io-buffer that have to be flushed/written to the external pendrive.

this is normal behaviour. same for windows. the only difference may be that others don't show finished while the buffer is not emptied.

---

