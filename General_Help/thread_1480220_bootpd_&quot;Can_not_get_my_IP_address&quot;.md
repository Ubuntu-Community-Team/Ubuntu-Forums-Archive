---
title: "bootpd: &quot;Can not get my IP address&quot;"
date: 2010-05-11
forum: General Help
---

### Post by burneverything on 2010-05-11
Hi
I'm trying to install over a network and followed the guide here:

When I try and start bootpd I get the error 
"Can not get my IP address" 

This seem to come from this part of the code:
```
/*
       * Get my hostname and IP address.
       */

      hep = gethostbyname(hostname);
      if (!hep) {
            fprintf(stderr, "Can not get my IP address\n");
            exit(1);
      }
      bcopy(hep->h_addr, (char *)&my_ip_addr, sizeof(my_ip_addr));

      if (standalone) 
```Am I right in assuming that it does not get its own IP address (ie the server) or am I mistaken and is it failing to get the IP address of the client I want to install to?

And if I am right how do I fix this problem?

---

