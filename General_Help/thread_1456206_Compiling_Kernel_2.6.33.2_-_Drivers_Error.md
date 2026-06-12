---
title: "Compiling Kernel 2.6.33.2 - Drivers Error"
date: 2010-04-16
forum: General Help
---

### Post by sab3156 on 2010-04-16
I am compiling kernel 2.6.33.2 in Ubuntu 9.10.  However, I receive this message along the way:[INDENT]**drivers/net/wireless/libertas/**[B]if_spi.c:59: error: field ‘spi_ready’ has incomplete type
drivers/net/wireless/libertas/[/B][B]if_spi.c:60: error: field ‘spi_thread_terminated’ has incomplete type
drivers/net/wireless/libertas/[/B][B]if_spi.c: In function ‘lbs_spi_thread’:
drivers/net/wireless/libertas/[/B][B]if_spi.c:785: error: implicit declaration of function ‘down_interruptible’
drivers/net/wireless/libertas/[/B][B]if_spi.c:787: error: implicit declaration of function ‘up’
drivers/net/wireless/libertas/[/B][B]if_spi.c: In function ‘if_spi_terminate_spi_thread’:
drivers/net/wireless/libertas/[/B][B]if_spi.c:834: error: implicit declaration of function ‘down’
drivers/net/wireless/libertas/[/B][B]if_spi.c: In function ‘if_spi_probe’:
drivers/net/wireless/libertas/[/B][B]if_spi.c:943: error: implicit declaration of function ‘sema_init’
make[4]: *** [drivers/net/wireless/[/B][B]libertas/if_spi.o] Error 1
make[3]: *** [drivers/net/wireless/[/B][B]libertas] Error 2
make[2]: *** [drivers/net/wireless] Error 2
make[1]: *** [drivers/net] Error 2
make: *** [drivers] Error 2[/B]
[/INDENT]I tried doing a:[INDENT][B]make clean
[/B][/INDENT]The same error occurred when I tried compiling again.  Is there something that must be done in order to get this compiled?

Thanks for your time.

---

### Post by sab3156 on 2010-04-16
EDIT:  Nevermind what I wrote below, I want to keep the wireless...


-------------

Since I am going to be using this as a server directly connected to the router, I don't really care for wireless... What would I need to disable in the kernel configuration to get past those errors above?

I disabled the *WiMAX Wireless Broadband Support* and now I want to know what I can disable under *Wireless*... everything?

---

### Post by darolu on 2010-04-17
I find it easier to use a .deb package, maybe it will work for you too:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/)

---

### Post by sab3156 on 2010-04-17
Thanks, darolu.  I actually used a different kernel (2.6.26.8) and it worked.  I hear that one is the best kernel for what I am doing with this server, anyway.

Now I have to fix grub, lol...  :lolflag:

---

### Post by -jay- on 2010-04-17
> **darolu said:**
> I find it easier to use a .deb package, maybe it will work for you too:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/)

i tried those but they install fine but after rebooting i had no mouse at all

---

