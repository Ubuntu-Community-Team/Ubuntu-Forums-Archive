---
title: "Cannot run program, no such file or directory"
date: 2011-01-14
forum: General Help
---

### Post by Fran2298 on 2011-01-14
When I try to run a program from the terminal, bash reports "No such file or directory", even though the file exists, is executable and I have permission to run it. The same program worked in the past, this behaviour is recent. Any suggestions?

---

### Post by TeoBigusGeekus on 2011-01-14
Could you post us the exact command you give, as well as the error messages?

---

### Post by cmoraes on 2011-01-14
if you're trying to run a file in your current directory, you need to use "./" before the command. e.g.

$  ./firefox-start

---

### Post by cmoraes on 2011-01-14
if you're trying to run a file in your current directory, you need to use "./" before the command. e.g.

$  ./firefox-start

---

### Post by oldos2er on 2011-01-14
If it's a 32-bit program, you'll need to install ia32-libs to run it.

---

### Post by oldos2er on 2011-01-14
If it's a 32-bit program, you'll need to install ia32-libs to run it.

---

### Post by Fran2298 on 2011-01-14
The exact program is Citrix client, /usr/lib/ICAClient/wfica. I am trying to run it by typing ./wfica  in /usr/lib/ICAClient/

---

### Post by Fran2298 on 2011-01-15
Thanks, the problem was with ia32-libs. When I removed wine, cleanup removed ia32-libs so Citrix reciever could no longer run. It was the 'file not found' message that confised me.

---

