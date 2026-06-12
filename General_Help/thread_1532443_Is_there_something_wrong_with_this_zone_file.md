---
title: "Is there something wrong with this zone file?"
date: 2010-07-16
forum: General Help
---

### Post by DrDoS on 2010-07-16
For the LIFE of me I can NOT get this domain to resolve properly.

Here is the zone file code

```
$TTL 14400
@       86400   SOA     ns1.reflectstudios.com. CMPRB1.custommyspaceprofiles.com.(
                                5052
                                86400
                                7200
                                3600000
                                86400
                        )
hotboyspot.com. 3600    IN      NS      ns1.reflectstudios.com.
hotbotspot.com. 3600    IN      NS      ns2.reflectstudios.com.

localhost.hotboyspot.com.       14400   IN      A       208.122.229.58

@       14400   IN      A       208.122.229.58
www     14400   IN      A       208.122.229.58

ftp     14400   IN      CNAME   @

hotboyspot.com.     14400   IN      MX      10      ASPMX.L.GOOGLE.COM.
hotboyspot.com.     14400   IN      MX      20      ALT1.ASPMX.L.GOOGLE.COM.
hotboyspot.com.     14400   IN      MX      20      ALT2.ASPMX.L.GOOGLE.COM.
hotboyspot.com.     14400   IN      MX      30      ASPMX2.GOOGLEMAIL.COM.
hotboyspot.com.     14400   IN      MX      30      ASPMX3.GOOGLEMAIL.COM.
hotboyspot.com.     14400   IN      MX      30      ASPMX4.GOOGLEMAIL.COM.
hotboyspot.com.     14400   IN      MX      30      ASPMX5.GOOGLEMAIL.COM.
```

am i doing something wrong here?

---

