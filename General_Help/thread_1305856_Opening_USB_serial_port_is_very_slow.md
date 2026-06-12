---
title: "Opening USB serial port is very slow"
date: 2009-10-30
forum: General Help
---

### Post by simus31 on 2009-10-30
Hi,

I am using a USB serial port that is using ftdi driver.
I am under Linux 2.6.29.

Something strange occured when opening the serial port. Sometimes the open is quite immediate but sometimes it takes ~20 seconds for the open to be done.

Moreover, once it takes long time to be opened, then it always takes this long for any other open.

The opening is done through my application where the code is as simple as follows:
    int fd;
    fd = open (devfile, O_RDWR | O_NOCTTY | O_NONBLOCK);

    if (fd == -1)
        return -1;
    close(fd);

Does anyone already experienced this kind of problems. Is there a way to get rid of this? What can be the cause?

Thanks and best regards!

---

