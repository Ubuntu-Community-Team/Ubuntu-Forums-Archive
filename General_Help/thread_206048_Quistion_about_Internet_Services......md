---
title: "Quistion about Internet Services....."
date: 2006-06-29
forum: General Help
---

### Post by shawnrgr on 2006-06-29
I have comcast cable right now, and i didn't have to set anything up to get anything working when I install any distros. I was considering switching to Verizon DSL 3.0mps. Its still "always on" i don't have to log in. My question is how compatible is linux with dsl. If I made the switch would i be able to just reboot and everything would be ok?

---

### Post by shawnrgr on 2006-06-29
also, what about verizon FiOS (Fiber Optic), anyone know if this will work with linux?

---

### Post by az on 2006-06-29
If you are able to connect to you ISP with a router, you will be able to do it in Ubuntu.  Most (or many) routers run linux inside....

If your DSl provider uses pppoe, you will have to run

sudo pppoeconf
from the command line once, to configure your connection.  There are nto a lot of people who connect their box directly to a pppoe source, and so there is no GUI for that.  So asides from having to drop to the command line the first time you connect, it will be painless.

---

