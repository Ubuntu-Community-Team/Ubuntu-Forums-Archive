---
title: "mpiexec.hydra"
date: 2011-09-13
forum: General Help
---

### Post by JCM_Pico on 2011-09-13
Hi there,

I've a task to run in a machine, but since it takes a while to run I would like to run it and then  quit session...
Usually I run this kind of things with nohup... but in this case I get this error:

H```
YDU_sock_read (./utils/sock/sock.c:222): read errno (Bad file descriptor)
control_cb (./pm/pmiserv/pmiserv_cb.c:249): assert (!closed) failed
HYDT_dmxu_poll_wait_for_event (./tools/demux/demux_poll.c:77): callback returned error status
HYD_pmci_wait_for_completion (./pm/pmiserv/pmiserv_pmci.c:206): error waiting for event
main (./ui/m
```pich/mpiexec.c:404): process manager error waiting for completion


How can I run mpiexec.hydra with nohup ????

---

### Post by JCM_Pico on 2011-09-17
bump

---

