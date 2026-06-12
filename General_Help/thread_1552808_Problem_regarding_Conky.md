---
title: "Problem regarding Conky"
date: 2010-08-14
forum: General Help
---

### Post by sbjaved on 2010-08-14
Hi,
I have conky 1.8.0 installed on my 10.04 system. I use this code to display free space in the partitions:
```
${fs_free /home} ${fs_bar 6 /home}$color
```
This used to work perfectly fine with fixed and removable drives but since a recent update (kernel?), the removable drives all seem to be mounted at a different path each time (e.g. /media/TOSHIBA EXT or /media/TOSHIBA EXT_ or any other variation) which naturally does not work with conky because the paths are explicitly specified. Does anybody know the problem and the solution?

---

### Post by ajgreeny on 2010-08-14
If the external disk partitions are labelled, using for example gparted, they will always mount in /media under that named folder, I think, which I assume should overcome your problem.

Make sure each label is different from any other, of course, or you could end up with the same problem.

---

### Post by sbjaved on 2010-09-12
Thankyou, this solved the problem. I used the Disk Utility instead of gparted.

---

