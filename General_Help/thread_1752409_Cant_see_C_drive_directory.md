---
title: "Cant see C drive directory"
date: 2011-05-07
forum: General Help
---

### Post by Kanith on 2011-05-07
How can I see a directory of the files on my C drive so that I can open them with Ubuntu?

---

### Post by garvinrick4 on 2011-05-07
> **Kanith said:**
> How can I see a directory of the files on my C drive so that I can open them with Ubuntu?
Are you using WUBI install or did you do a partition install:
In WUBI:
File system /hosts
If not Wubi tell me us what version you are using 11.04, 10.10 ,10.04
```
lsb_release -a
``` in a terminal:

---

### Post by Kanith on 2011-05-07
I installed wubi, i think. I am new to linux and see a lot of computer jargon that I don't understand. 

Can't there be a simple button to click to see the files on the C drive?

---

### Post by garvinrick4 on 2011-05-07
Open the file system under Places drop down menu and there will be one that says "host", open it up. That is as simple as it gets. No buttons just part of file system. Been that way since Wubi has been out. 
Windows is the "host" system to your linux install of Ubuntu Wubi.

---

