---
title: "Ubuntu without gdm but with xdmcp?"
date: 2010-08-27
forum: General Help
---

### Post by ubit on 2010-08-27
Hi,

for my small home server i want the machine to NOT start x11 automatically but to enable remote logins via xdmcp.
The problem: xdmcp is controlled by gdm. If i disable gdm to have no x11-login-screen xdmcp does not run...

Is there any way to start gdm without starting x11 on the console?

Ciao, Udo

---

### Post by GlazedDonut on 2010-08-27
I dont think so because gdm is reliant on X in order to work.

---

### Post by ubit on 2010-08-27
Hi,

i am currently trying a solution based on FreeNX. Seems to work. I disabled gdm (by requiring runlevel 3 for gdm startup in /etc/init/gdm.conf) and i am still able to connect to the ubuntu-system with a FreeNX Client from Windows. Works - but the FreeNX-Client is not very stable on Vista x64.
And it runs slow compared to Xming with xdmcp.

Ciao, Udo

---

