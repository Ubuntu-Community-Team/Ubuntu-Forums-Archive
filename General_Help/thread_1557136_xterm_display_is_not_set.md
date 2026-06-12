---
title: "xterm: display is not set"
date: 2010-08-20
forum: General Help
---

### Post by dersu on 2010-08-20
Hi,
I've just installed xterm, ant trying to run it from my windows machine using ssh.

I have X11Forwarding yes on /etc/ssh/sshd_config

when I use, MobaXterm, np, I can use xterm after I log
ssh -X xxx

but when I use Cygwin, and do ssh -X xxx, and then xterm,
I have: xterm XT error : Can't open display :
xterm: Display is not set

help please. I prefer Cygwin.

---

### Post by Brandon Williams on 2010-08-22
Is cygwin running an X server for you? What is the value of $DISPLAY in cygwin before running ssh?

---

### Post by dersu on 2010-08-23
thanks for you response.
I ve installed Xming on windows. but when I type $DISPLAY on cygwin it gives me an emtpy line. and the same error message to xterm.

---

### Post by Brandon Williams on 2010-08-24
It sounds like cygwin isn't fully aware of your running Xming instance. Try setting the display variable at the cygwin command line:
```
export DISPLAY=localhost:0.0
```
After that, can you start an xterm from within cygwin? Or run any other X application? If you can run X applications locally from within cygwin, then try forwarding X over an ssh connection again.

---

