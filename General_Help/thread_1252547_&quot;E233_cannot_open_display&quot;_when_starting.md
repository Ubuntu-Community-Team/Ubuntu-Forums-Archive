---
title: "&quot;E233: cannot open display&quot; when starting gvim on root shell"
date: 2009-08-29
forum: General Help
---

### Post by tsanchung on 2009-08-29
"sudo gvim" is ok on a non-root shell.
 $ sudo gvim /etc/fstab
[sudo] password for ts:

However, "E233: cannot open display" error appears when starting gvim on ubuntu 8.04 root shell.
# DISPLAY=localhost:0.0
# xclock
Error: Can't open display: localhost:0.0
# gvim /etc/fstab
E233: cannot open display
Press ENTER or type command to continue
# kdesudo gvim  /etc/fstab
kdesudo: cannot connect to X server



# DISPLAY=:0.0
# xclock
Invalid MIT-MAGIC-COOKIE-1 keyError: Can't open display: :0.0
# DISPLAY=:0
# xclock
Invalid MIT-MAGIC-COOKIE-1 keyError: Can't open display: :0

---

