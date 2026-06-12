---
title: "Trying to configure DNTV Live Pro TV card"
date: 2006-04-18
forum: General Help
---

### Post by Pretzal on 2006-04-18
Am trying to configure the digitalnow DNTV Live! DVB-T Pro TV Card but come up with the following error:

root@Ubuntu:/home/me/DNTV# sh DVB-Build.sh build

Warning: Your kernel appears to have DVB support already
built as modules.

Depending on your distribution, you may need to do a:
    ./DVB-Build remove-symbols
    ./DVB-Build clean
    ./DVB-Build
before you will be able to use load your drivers successfully.

(This build will continue in 5 seconds)

make -C /lib/modules/2.6.12-10-686/build SUBDIRS=/home/me/DNTV/video4linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-686'
  CC [M]  /home/me/DNTV/video4linux/video-buf.o
  CC [M]  /home/me/DNTV/video4linux/v4l1-compat.o
  CC [M]  /home/me/DNTV/video4linux/v4l2-common.o
  CC [M]  /home/me/DNTV/video4linux/btcx-risc.o
  CC [M]  /home/me/DNTV/video4linux/ir-common.o
  CC [M]  /home/me/DNTV/video4linux/bttv-driver.o
  CC [M]  /home/me/DNTV/video4linux/bttv-cards.o
  CC [M]  /home/me/DNTV/video4linux/bttv-risc.o
  CC [M]  /home/me/DNTV/video4linux/bttv-if.o
  CC [M]  /home/me/DNTV/video4linux/bttv-vbi.o
  CC [M]  /home/me/DNTV/video4linux/bttv-i2c.o
/home/me/DNTV/video4linux/bttv-i2c.c:336: error: unknown field `id' specifi ed in initializer
/home/me/DNTV/video4linux/bttv-i2c.c:336: warning: missing braces around in itializer
/home/me/DNTV/video4linux/bttv-i2c.c:336: warning: (near initialization for  `bttv_i2c_client_template.released')
make[2]: *** [/home/me/DNTV/video4linux/bttv-i2c.o] Error 1
make[1]: *** [_module_/home/me/DNTV/video4linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-686'
make: *** [default] Error 2
root@Ubuntu:/home/me/DNTV#

The linux driver I am trying to configure can be found here:

[http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DNTV/](http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DNTV/)

Does anyone have any clues?

Thanks in advance

---

### Post by Pretzal on 2006-04-20
Does anyone have any clues?

---

### Post by zzirf on 2007-06-13
> **Pretzal said:**
> Am trying to configure the digitalnow DNTV Live! DVB-T Pro TV Card but come up with the following error:

root@Ubuntu:/home/me/DNTV# sh DVB-Build.sh build

Warning: Your kernel appears to have DVB support already
built as modules.

Depending on your distribution, you may need to do a:
    ./DVB-Build remove-symbols
    ./DVB-Build clean
    ./DVB-Build
before you will be able to use load your drivers successfully.

(This build will continue in 5 seconds)

make -C /lib/modules/2.6.12-10-686/build SUBDIRS=/home/me/DNTV/video4linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-686'
  CC [M]  /home/me/DNTV/video4linux/video-buf.o
  CC [M]  /home/me/DNTV/video4linux/v4l1-compat.o
  CC [M]  /home/me/DNTV/video4linux/v4l2-common.o
  CC [M]  /home/me/DNTV/video4linux/btcx-risc.o
  CC [M]  /home/me/DNTV/video4linux/ir-common.o
  CC [M]  /home/me/DNTV/video4linux/bttv-driver.o
  CC [M]  /home/me/DNTV/video4linux/bttv-cards.o
  CC [M]  /home/me/DNTV/video4linux/bttv-risc.o
  CC [M]  /home/me/DNTV/video4linux/bttv-if.o
  CC [M]  /home/me/DNTV/video4linux/bttv-vbi.o
  CC [M]  /home/me/DNTV/video4linux/bttv-i2c.o
/home/me/DNTV/video4linux/bttv-i2c.c:336: error: unknown field `id' specifi ed in initializer
/home/me/DNTV/video4linux/bttv-i2c.c:336: warning: missing braces around in itializer
/home/me/DNTV/video4linux/bttv-i2c.c:336: warning: (near initialization for  `bttv_i2c_client_template.released')
make[2]: *** [/home/me/DNTV/video4linux/bttv-i2c.o] Error 1
make[1]: *** [_module_/home/me/DNTV/video4linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-686'
make: *** [default] Error 2
root@Ubuntu:/home/me/DNTV#

The linux driver I am trying to configure can be found here:

[http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DNTV/](http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DNTV/)

Does anyone have any clues?

Thanks in advance

Hi Pretzel,

That is exactly the message I get too.  I suspect that you have got further down the track than this by now so can you tell me at least how you got kaffeine to run from this point above on ward?  I am new to ubuntu and I do not really understand the jargon but I am good at following directions.

Hope you can help me out now,

---

