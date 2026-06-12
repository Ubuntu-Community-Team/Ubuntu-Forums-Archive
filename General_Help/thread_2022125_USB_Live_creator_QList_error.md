---
title: "USB Live creator QList error"
date: 2012-07-10
forum: General Help
---

### Post by imaginarythomas on 2012-07-10
I'm trying to build a bootable SD card for a raspberry pi but the liveusb-creator fails with this mysterious error when I try to browse for an image

```

ASSERT failure in QList<T>::at: "index out of range", file ../../include/QtCore/../../src/corelib/tools/qlist.h, line 391

```

I can't find anyone else who has had this problem, I guess I'm just lucky.

Anyone have any insight?

I'm on ubuntu 8.04 because the dell mini preload disallows upgrading.

---

### Post by Cheesemill on 2012-07-10
I don't think that you can use the Live USB creater to set up a card for a Raspberry Pi as it has a non-standard method of booting (the bootloader is store in the GPU binary blob).

Also Ubuntu won't work on a Raspberry Pi, you need to use one of the supported distros (just Debian and Arch at the moment).

To set up the SD card you need to download one of the image files and use dd to transfer it.

For more info on how to set up an SD card and OS see:
[http://www.raspberrypi.org/downloads](http://www.raspberrypi.org/downloads)

---

### Post by imaginarythomas on 2012-07-10
Oh, I'm not installing ubuntu on the SD card, I'm installing the debian squeeze.

I  just use this tool to make bootable devices. It worked last time I did this but has since stopped.

I've also tried live usb install and I get another error:

```

Traceback (most recent call last):
  File "./live-usb-install.py", line 19, in <module>
    import asubprocess
  File "/usr/share/live-usb-install/asubprocess.py", line 467
    process = Popen(*popenargs, stdout=PIPE, **kwargs)
                                     ^

```

I tried using dd as instructed on the site but it seems to stop prematurely and the SD card will not boot

---

### Post by Cheesemill on 2012-07-10
Even if you could get the application to work, it wouldn't create an SD card that would boot on the Pi.

I doubt you will get any help with this as 8.04 is now end-of-life and doesn't receive support or updates any more.

Can you post the dd command you have tried and the output it gives you, I may be able to help with that.

---

