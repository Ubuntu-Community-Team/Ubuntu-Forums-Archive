---
title: "ERROR: Unable to bind to port"
date: 2010-12-29
forum: General Help
---

### Post by labud on 2010-12-29
64 bit lubuntu

trying to start a .bin file from desktop

gone to properties of file and made executable
 open folder where .bin resides 
 open terminal
 > dabud@GG64bit:~/Desktop/WCS185b32010b$ ./wcs185b3.bin
29/12/2010 00:37:00 Loading Config...
29/12/2010 00:37:00 Config Loaded
29/12/2010 00:37:00 Loading IP to Country Data
29/12/2010 00:37:00 IP to Country Database Imported
29/12/2010 00:37:00 WCS 1.8.5b3-Linux
**29/12/2010 00:37:00 ERROR: Unable to bind to port**
dabud@GG64bit:~/Desktop/WCS185b32010b$ 

anyone have any idea what this means
I have never run into it before

I am thinking it might be internet related, but have no idea how to solve this problem.
Google does come up with things re the error but I am not clear as to what I should do.
WCS 1.8.5b3-Linux is a chat program

Any ideas where I might start?
Thanks

---

### Post by dcstar on 2010-12-29
> **labud said:**
> 64 bit lubuntu

trying to start a .bin file from desktop

gone to properties of file and made executable
 open folder where .bin resides 
 open terminal
 
anyone have any idea what this means
I have never run into it before

I am thinking it might be internet related, but have no idea how to solve this problem.
Google does come up with things re the error but I am not clear as to what I should do.
**WCS 1.8.5b3-Linux is a chat program**

Any ideas where I might start?
Thanks

There is probably an existing "Chat program" already using the port.

Do not "quote" code.

---

### Post by labud on 2010-12-29
sry, should I have used CODE tags?

the port I am using is 65535.

I didn't see that anything is using this port, but to be sure I changed the port to 55535 and tried to connect.  Using 55535 tcp, it worked.

Thanks for direction, dcstar.

---

