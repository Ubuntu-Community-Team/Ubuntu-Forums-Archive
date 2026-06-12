---
title: "How start programs via SSH?"
date: 2009-12-12
forum: General Help
---

### Post by mac666 on 2009-12-12
Hey
If i try to start some programs via SSH, on a remote computer, 
the programs dies when i close my SSH. 

How could i start the programs on the remote computer via SSH? :|

---

### Post by squaregoldfish on 2009-12-12
Use the nohup command:
```

nohup <program command> &
```This will prevent the program being killed. Any console output from the program will not be displayed, but instead is recorded in a file named nohup.out.

Steve.

---

### Post by lmarmisa on 2009-12-12
ssh opens a shell in a remote computer using a secure channel. But this shell has the same properties than any other shell. Therefore, if you abort a shell, the ongoing commands of this shell are also aborted.

If you want that a command does not abort when you close the ssh, then use **nohup**:

```
**nohup command &**
```Best regards,

Luis

---

### Post by mac666 on 2009-12-12
Thanks guys! Thats great!

---

### Post by Wardje on 2009-12-12
Note that if you want greater control of things (getting back to the program later and the likes), you might want to have a look into `screen' instead.

---

