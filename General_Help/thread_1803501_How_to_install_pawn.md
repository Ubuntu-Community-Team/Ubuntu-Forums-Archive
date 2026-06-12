---
title: "How to install pawn"
date: 2011-07-13
forum: General Help
---

### Post by Nerijus1 on 2011-07-13
Hello all!,
I'm trying to install pawn for linux (downloaded from here: [http://www.compuphase.com/pawn/pawn.htm#DOWNLOAD_PKG](http://www.compuphase.com/pawn/pawn.htm#DOWNLOAD_PKG))
and can anyone help me, and say how to install pawn-3.3.4127.project file ?
Big thanks for answer!

---

### Post by WorMzy on 2011-07-13
It's a bash script. Make it executable, then run it from a terminal.

```
#make it executable:
chmod +x pawn-3.3.4127.project
#run it:
./pawn-3.3.4127.project
```

---

### Post by Nerijus1 on 2011-07-13
Big thanks for help!

---

### Post by WorMzy on 2011-07-13
Forgot to mention that you may need to use sudo with it.

If you get a "permission denied" error when you run ./pawn-3.3.4127.project, try running
```
sudo ./pawn-3.3.4127.project
```

---

