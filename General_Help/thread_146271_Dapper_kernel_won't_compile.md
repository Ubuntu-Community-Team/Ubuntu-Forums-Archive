---
title: "Dapper kernel won't compile"
date: 2006-03-18
forum: General Help
---

### Post by kkinder on 2006-03-18
When I try to compile my dapper 2.6.15 kernel, with stock config or by loading /boot/config-2.6.15, I get this rather weird message:

```

  CC [M]  drivers/usb/net/zd1211/zdusb.o
In file included from drivers/usb/net/zd1211/zdusb.c:41:
drivers/usb/net/zd1211/zddevlist.h:7:2: error: #error "Error in source file, line 35"
make[4]: *** [drivers/usb/net/zd1211/zdusb.o] Error 1
make[3]: *** [drivers/usb/net/zd1211] Error 2
make[2]: *** [drivers/usb/net] Error 2
make[1]: *** [drivers/usb] Error 2
make: *** [drivers] Error 2

```

zddevlist.h looks like this, which is a but confusing, but I'm rolling with it:

```

/*
 * This is auto generated file, do not edit manualy.
 *
 * Source file version:
 *      $Id: zddevlist,v 1.5 2005/08/20 10:21:47 sagamore Exp $
 */
#error "Error in source file, line 35"

#define VENDOR_


#define ZD1211_IDS \
        { } /* Terminating entry */

char * zd1211_ids_description [] = {
        NULL /* Terminating entry */
};

```

So it looks like whatever generates this file is busted. What's going on here?

---

