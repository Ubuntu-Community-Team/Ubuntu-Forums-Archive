---
title: "MCS9865 serial card in 10.04"
date: 2010-07-29
forum: General Help
---

### Post by Grenage on 2010-07-29
Greetings!

I'm attempting to compile drivers for a Moschip MCS9865, but it's failing horrifically.  This is due to a recent kernel, because it doesn't happen with older kernels.  Has anyone run into this, and found a way around it?

I've e-mailed Moschip, but am not holding out much hope.  The errors are as follows:

```
root@skynet:~/MCS9865_Linux/MCS9865_V1.0.0.6# make
rm -f *.mod.c *.o *.ko .*.cmd *.symvers
make -C /lib/modules/2.6.32-21-generic-pae/build/ SUBDIRS=/root/MCS9865_Linux/MCS9865_V1.0.0.6 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic-pae'
  CC [M]  /root/MCS9865_Linux/MCS9865_V1.0.0.6/mcs9865.o
/root/MCS9865_Linux/MCS9865_V1.0.0.6/mcs9865.c: In function ‘serial9865_start_tx’:
/root/MCS9865_Linux/MCS9865_V1.0.0.6/mcs9865.c:498: error: ‘struct uart_port’ has no member named ‘info’
/root/MCS9865_Linux/MCS9865_V1.0.0.6/mcs9865.c: In function ‘check_modem_status’:
/root/MCS9865_Linux/MCS9865_V1.0.0.6/mcs9865.c:611: error: ‘struct uart_port’ has no member named ‘info’
/root/MCS9865_Linux/MCS9865_V1.0.0.6/mcs9865.c: In function ‘receive_chars’:
/root/MCS9865_Linux/MCS9865_V1.0.0.6/mcs9865.c:625: error: ‘struct uart_port’ has no member named ‘info’
/root/MCS9865_Linux/MCS9865_V1.0.0.6/mcs9865.c:633: warning: comparison of distinct pointer types lacks a cast
/root/MCS9865_Linux/MCS9865_V1.0.0.6/mcs9865.c:707: warning: comparison of distinct pointer types lacks a cast
/root/MCS9865_Linux/MCS9865_V1.0.0.6/mcs9865.c: In function ‘transmit_chars’:
/root/MCS9865_Linux/MCS9865_V1.0.0.6/mcs9865.c:715: error: ‘struct uart_port’ has no member named ‘info’
/root/MCS9865_Linux/MCS9865_V1.0.0.6/mcs9865.c: In function ‘transmit_chars_dma_stop_done’:
/root/MCS9865_Linux/MCS9865_V1.0.0.6/mcs9865.c:760: error: ‘struct uart_port’ has no member named ‘info’
/root/MCS9865_Linux/MCS9865_V1.0.0.6/mcs9865.c: In function ‘transmit_chars_dma_done’:
/root/MCS9865_Linux/MCS9865_V1.0.0.6/mcs9865.c:776: error: ‘struct uart_port’ has no member named ‘info’
/root/MCS9865_Linux/MCS9865_V1.0.0.6/mcs9865.c: In function ‘receive_chars_dma_done’:
/root/MCS9865_Linux/MCS9865_V1.0.0.6/mcs9865.c:862: error: ‘struct uart_port’ has no member named ‘info’
/root/MCS9865_Linux/MCS9865_V1.0.0.6/mcs9865.c: In function ‘serial9865_handle_port’:
/root/MCS9865_Linux/MCS9865_V1.0.0.6/mcs9865.c:973: error: ‘struct uart_port’ has no member named ‘info’
make[2]: *** [/root/MCS9865_Linux/MCS9865_V1.0.0.6/mcs9865.o] Error 1
make[1]: *** [_module_/root/MCS9865_Linux/MCS9865_V1.0.0.6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic-pae'
make: *** [default] Error 2

```

Russell.

---

### Post by Grenage on 2010-07-30
I stand corrected, and am impressed; Moschip sent me a new set of drivers (1.0.0.9) that compile fine.  They aren't on their website at the moment, but they will mail them to you.

---

### Post by StrangeMan on 2010-08-18
Where can I get these drivers? I got the same card here and the same problem.

StrangeMan

---

### Post by Sniper on 2010-10-10
Can You please upload the driver somewhere and post a link. I got the same problems as you, and don't want to downgrade ubuntu.

---

