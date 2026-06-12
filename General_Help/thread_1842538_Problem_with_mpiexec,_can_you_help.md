---
title: "Problem with mpiexec, can you help?"
date: 2011-09-11
forum: General Help
---

### Post by JCM_Pico on 2011-09-11
Hi there

 I'm trying to run a heavy computing in a computer with 4 processor (2 in one node and 2 in other node). 
the command I was instructed to give to run it is something like:

```
 /usr/local/bin/mpiexec.hydra -f /home/pico/hydra.host -np 4 /bin/bash -c "ulimit -s unlimited ; ./real" 
``` 

everything runs fine when I do it in terminal, but if I try to run it with nohup, in order to live running after logging off from the workstation this error occurs ...

```
HYDU_sock_read (./utils/sock/sock.c:222): read errno (Bad file descriptor)
control_cb (./pm/pmiserv/pmiserv_cb.c:249): assert (!closed) failed
HYDT_dmxu_poll_wait_for_event (./tools/demux/demux_poll.c:77): callback returned error status
HYD_pmci_wait_for_completion (./pm/pmiserv/pmiserv_pmci.c:206): error waiting for event
main (./ui/mpich/mpiexec.c:404): process manager error waiting for completion
HYDU_sock_read (./utils/sock/sock.c:222): read errno (Bad file descriptor)
control_cb (./pm/pmiserv/pmiserv_cb.c:249): assert (!closed) failed
HYDT_dmxu_poll_wai_for_event (./tools/demux/demux_poll.c:77): callback returned error status
HYD_pmci_wait_for_completion (./pm/pmiserv/pmiserv_pmci.c:206): error waiting for event
main (./ui/mpich/mpiexec.c:404): process manager error waiting for completion

```

Do you know some workaround to this???

---

### Post by JCM_Pico on 2011-09-17
bump

---

