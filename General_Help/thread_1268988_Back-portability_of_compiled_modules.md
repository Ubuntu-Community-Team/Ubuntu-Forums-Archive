---
title: "Back-portability of compiled modules?"
date: 2009-09-17
forum: General Help
---

### Post by aka_bigred on 2009-09-17
I am wondering if I can run/install a module that I compiled in Ubuntu 2.6.24 into another PC running version 2.6.17 ?  Can I just copy over the *.ko file to the old machine and insmod it?

I have a module that I can't get to compile on my old server but will compile on a different machine with a newer Ubuntu install. The module in question is a USB driver for communicating with my new beefier UPS.  Unfortunately I won't be able to upgrade the OS on the target PC until this winter when I have more time.  

Is this possible, or will it fail & crash my machine?

---

### Post by aka_bigred on 2009-09-18
Anyone????

---

### Post by Whiffle on 2009-09-18
You can try it, but I don't think it will work.  

Why won't it compile?

---

### Post by warp99 on 2009-09-18
It depends. If the source and the dependencies of the module has not changed from one kernel to the next the module may work, but most of the time it does not. Since you're going backwards with the kernel revisions I highly doubt that would work

I would check if there's an older version of the source code and try to compile that if there are no security issues. Since it's just a UPS module I don't think that would be a problem. You may lose some features by doing this, but at least it would work. Also check with the developer. He/she may have some additional information to help you.

---

### Post by aka_bigred on 2009-09-18
> **Whiffle said:**
> You can try it, but I don't think it will work.  

Why won't it compile?

There seems to be some significant missing dependancies of some kind.  I'm newer to compiling under Linux - ie I can do it when everything goes well :).  Here's the output when I try to compile:


```

make -C /lib/modules/2.6.17-10-server/build M=/usr/src/modules modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-server'
  CC [M]  /usr/src/modules/cypress_m8.o
/usr/src/modules/cypress_m8.c:119: error: &#8216;usb_serial_probe&#8217; undeclared here (not in a function)
/usr/src/modules/cypress_m8.c:120: error: &#8216;usb_serial_disconnect&#8217; undeclared here (not in a function)
/usr/src/modules/cypress_m8.c:148: error: field &#8216;tmp_termios&#8217; has incomplete type
/usr/src/modules/cypress_m8.c:160: warning: &#8216;struct usb_serial&#8217; declared inside parameter list
/usr/src/modules/cypress_m8.c:160: warning: its scope is only this definition or declaration, which is probably not what you want
/usr/src/modules/cypress_m8.c:161: warning: &#8216;struct usb_serial&#8217; declared inside parameter list
/usr/src/modules/cypress_m8.c:162: warning: &#8216;struct usb_serial&#8217; declared inside parameter list
/usr/src/modules/cypress_m8.c:163: warning: &#8216;struct usb_serial&#8217; declared inside parameter list
/usr/src/modules/cypress_m8.c:164: warning: &#8216;struct usb_serial_port&#8217; declared inside parameter list
/usr/src/modules/cypress_m8.c:165: warning: &#8216;struct usb_serial_port&#8217; declared inside parameter list
/usr/src/modules/cypress_m8.c:166: warning: &#8216;struct usb_serial_port&#8217; declared inside parameter list
/usr/src/modules/cypress_m8.c:167: warning: &#8216;struct usb_serial_port&#8217; declared inside parameter list
/usr/src/modules/cypress_m8.c:168: warning: &#8216;struct usb_serial_port&#8217; declared inside parameter list
/usr/src/modules/cypress_m8.c:169: warning: &#8216;struct usb_serial_port&#8217; declared inside parameter list
/usr/src/modules/cypress_m8.c:170: warning: &#8216;struct usb_serial_port&#8217; declared inside parameter list
/usr/src/modules/cypress_m8.c:171: warning: &#8216;struct usb_serial_port&#8217; declared inside parameter list
/usr/src/modules/cypress_m8.c:172: warning: &#8216;struct usb_serial_port&#8217; declared inside parameter list
/usr/src/modules/cypress_m8.c:173: warning: &#8216;struct usb_serial_port&#8217; declared inside parameter list
/usr/src/modules/cypress_m8.c:174: warning: &#8216;struct usb_serial_port&#8217; declared inside parameter list
/usr/src/modules/cypress_m8.c:175: warning: &#8216;struct usb_serial_port&#8217; declared inside parameter list
/usr/src/modules/cypress_m8.c:176: warning: &#8216;struct usb_serial_port&#8217; declared inside parameter list
/usr/src/modules/cypress_m8.c:192: error: variable &#8216;cypress_earthmate_device&#8217; has initializer but incomplete type
/usr/src/modules/cypress_m8.c:193: error: unknown field &#8216;driver&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:193: error: extra brace group at end of initializer
/usr/src/modules/cypress_m8.c:193: error: (near initialization for &#8216;cypress_earthmate_device&#8217;)
/usr/src/modules/cypress_m8.c:196: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:196: warning: (near initialization for &#8216;cypress_earthmate_device&#8217;)
/usr/src/modules/cypress_m8.c:197: error: unknown field &#8216;description&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:197: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:197: warning: (near initialization for &#8216;cypress_earthmate_device&#8217;)
/usr/src/modules/cypress_m8.c:198: error: unknown field &#8216;usb_driver&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:198: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:198: warning: (near initialization for &#8216;cypress_earthmate_device&#8217;)
/usr/src/modules/cypress_m8.c:199: error: unknown field &#8216;id_table&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:199: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:199: warning: (near initialization for &#8216;cypress_earthmate_device&#8217;)
/usr/src/modules/cypress_m8.c:200: error: unknown field &#8216;num_interrupt_in&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:200: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:200: warning: (near initialization for &#8216;cypress_earthmate_device&#8217;)
/usr/src/modules/cypress_m8.c:201: error: unknown field &#8216;num_interrupt_out&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:201: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:201: warning: (near initialization for &#8216;cypress_earthmate_device&#8217;)
/usr/src/modules/cypress_m8.c:202: error: unknown field &#8216;num_bulk_in&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:202: error: &#8216;NUM_DONT_CARE&#8217; undeclared here (not in a function)
/usr/src/modules/cypress_m8.c:202: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:202: warning: (near initialization for &#8216;cypress_earthmate_device&#8217;)
/usr/src/modules/cypress_m8.c:203: error: unknown field &#8216;num_bulk_out&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:203: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:203: warning: (near initialization for &#8216;cypress_earthmate_device&#8217;)
/usr/src/modules/cypress_m8.c:204: error: unknown field &#8216;num_ports&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:204: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:204: warning: (near initialization for &#8216;cypress_earthmate_device&#8217;)
/usr/src/modules/cypress_m8.c:205: error: unknown field &#8216;attach&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:205: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:205: warning: (near initialization for &#8216;cypress_earthmate_device&#8217;)
/usr/src/modules/cypress_m8.c:206: error: unknown field &#8216;shutdown&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:206: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:206: warning: (near initialization for &#8216;cypress_earthmate_device&#8217;)
/usr/src/modules/cypress_m8.c:207: error: unknown field &#8216;open&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:207: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:207: warning: (near initialization for &#8216;cypress_earthmate_device&#8217;)
/usr/src/modules/cypress_m8.c:208: error: unknown field &#8216;close&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:208: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:208: warning: (near initialization for &#8216;cypress_earthmate_device&#8217;)
/usr/src/modules/cypress_m8.c:209: error: unknown field &#8216;write&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:209: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:209: warning: (near initialization for &#8216;cypress_earthmate_device&#8217;)
/usr/src/modules/cypress_m8.c:210: error: unknown field &#8216;write_room&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:210: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:210: warning: (near initialization for &#8216;cypress_earthmate_device&#8217;)
/usr/src/modules/cypress_m8.c:211: error: unknown field &#8216;ioctl&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:211: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:211: warning: (near initialization for &#8216;cypress_earthmate_device&#8217;)
/usr/src/modules/cypress_m8.c:212: error: unknown field &#8216;set_termios&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:212: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:212: warning: (near initialization for &#8216;cypress_earthmate_device&#8217;)
/usr/src/modules/cypress_m8.c:213: error: unknown field &#8216;tiocmget&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:213: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:213: warning: (near initialization for &#8216;cypress_earthmate_device&#8217;)
/usr/src/modules/cypress_m8.c:214: error: unknown field &#8216;tiocmset&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:214: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:214: warning: (near initialization for &#8216;cypress_earthmate_device&#8217;)
/usr/src/modules/cypress_m8.c:215: error: unknown field &#8216;chars_in_buffer&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:215: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:215: warning: (near initialization for &#8216;cypress_earthmate_device&#8217;)
/usr/src/modules/cypress_m8.c:216: error: unknown field &#8216;throttle&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:216: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:216: warning: (near initialization for &#8216;cypress_earthmate_device&#8217;)
/usr/src/modules/cypress_m8.c:217: error: unknown field &#8216;unthrottle&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:217: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:217: warning: (near initialization for &#8216;cypress_earthmate_device&#8217;)
/usr/src/modules/cypress_m8.c:218: error: unknown field &#8216;read_int_callback&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:218: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:218: warning: (near initialization for &#8216;cypress_earthmate_device&#8217;)
/usr/src/modules/cypress_m8.c:219: error: unknown field &#8216;write_int_callback&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:219: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:219: warning: (near initialization for &#8216;cypress_earthmate_device&#8217;)
/usr/src/modules/cypress_m8.c:222: error: variable &#8216;cypress_hidcom_device&#8217; has initializer but incomplete type
/usr/src/modules/cypress_m8.c:223: error: unknown field &#8216;driver&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:223: error: extra brace group at end of initializer
/usr/src/modules/cypress_m8.c:223: error: (near initialization for &#8216;cypress_hidcom_device&#8217;)
/usr/src/modules/cypress_m8.c:226: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:226: warning: (near initialization for &#8216;cypress_hidcom_device&#8217;)
/usr/src/modules/cypress_m8.c:227: error: unknown field &#8216;description&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:227: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:227: warning: (near initialization for &#8216;cypress_hidcom_device&#8217;)
/usr/src/modules/cypress_m8.c:228: error: unknown field &#8216;usb_driver&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:228: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:228: warning: (near initialization for &#8216;cypress_hidcom_device&#8217;)
/usr/src/modules/cypress_m8.c:229: error: unknown field &#8216;id_table&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:229: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:229: warning: (near initialization for &#8216;cypress_hidcom_device&#8217;)
/usr/src/modules/cypress_m8.c:230: error: unknown field &#8216;num_interrupt_in&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:230: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:230: warning: (near initialization for &#8216;cypress_hidcom_device&#8217;)
/usr/src/modules/cypress_m8.c:231: error: unknown field &#8216;num_interrupt_out&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:231: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:231: warning: (near initialization for &#8216;cypress_hidcom_device&#8217;)
/usr/src/modules/cypress_m8.c:232: error: unknown field &#8216;num_bulk_in&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:232: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:232: warning: (near initialization for &#8216;cypress_hidcom_device&#8217;)
/usr/src/modules/cypress_m8.c:233: error: unknown field &#8216;num_bulk_out&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:233: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:233: warning: (near initialization for &#8216;cypress_hidcom_device&#8217;)
/usr/src/modules/cypress_m8.c:234: error: unknown field &#8216;num_ports&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:234: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:234: warning: (near initialization for &#8216;cypress_hidcom_device&#8217;)
/usr/src/modules/cypress_m8.c:235: error: unknown field &#8216;attach&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:235: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:235: warning: (near initialization for &#8216;cypress_hidcom_device&#8217;)
/usr/src/modules/cypress_m8.c:236: error: unknown field &#8216;shutdown&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:236: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:236: warning: (near initialization for &#8216;cypress_hidcom_device&#8217;)
/usr/src/modules/cypress_m8.c:237: error: unknown field &#8216;open&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:237: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:237: warning: (near initialization for &#8216;cypress_hidcom_device&#8217;)
/usr/src/modules/cypress_m8.c:238: error: unknown field &#8216;close&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:238: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:238: warning: (near initialization for &#8216;cypress_hidcom_device&#8217;)
/usr/src/modules/cypress_m8.c:239: error: unknown field &#8216;write&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:239: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:239: warning: (near initialization for &#8216;cypress_hidcom_device&#8217;)
/usr/src/modules/cypress_m8.c:240: error: unknown field &#8216;write_room&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:240: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:240: warning: (near initialization for &#8216;cypress_hidcom_device&#8217;)
/usr/src/modules/cypress_m8.c:241: error: unknown field &#8216;ioctl&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:241: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:241: warning: (near initialization for &#8216;cypress_hidcom_device&#8217;)
/usr/src/modules/cypress_m8.c:242: error: unknown field &#8216;set_termios&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:242: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:242: warning: (near initialization for &#8216;cypress_hidcom_device&#8217;)
/usr/src/modules/cypress_m8.c:243: error: unknown field &#8216;tiocmget&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:243: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:243: warning: (near initialization for &#8216;cypress_hidcom_device&#8217;)
/usr/src/modules/cypress_m8.c:244: error: unknown field &#8216;tiocmset&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:244: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:244: warning: (near initialization for &#8216;cypress_hidcom_device&#8217;)
/usr/src/modules/cypress_m8.c:245: error: unknown field &#8216;chars_in_buffer&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:245: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:245: warning: (near initialization for &#8216;cypress_hidcom_device&#8217;)
/usr/src/modules/cypress_m8.c:246: error: unknown field &#8216;throttle&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:246: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:246: warning: (near initialization for &#8216;cypress_hidcom_device&#8217;)
/usr/src/modules/cypress_m8.c:247: error: unknown field &#8216;unthrottle&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:247: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:247: warning: (near initialization for &#8216;cypress_hidcom_device&#8217;)
/usr/src/modules/cypress_m8.c:248: error: unknown field &#8216;read_int_callback&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:248: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:248: warning: (near initialization for &#8216;cypress_hidcom_device&#8217;)
/usr/src/modules/cypress_m8.c:249: error: unknown field &#8216;write_int_callback&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:249: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:249: warning: (near initialization for &#8216;cypress_hidcom_device&#8217;)
/usr/src/modules/cypress_m8.c:252: error: variable &#8216;cypress_ca42v2_device&#8217; has initializer but incomplete type
/usr/src/modules/cypress_m8.c:253: error: unknown field &#8216;driver&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:253: error: extra brace group at end of initializer
/usr/src/modules/cypress_m8.c:253: error: (near initialization for &#8216;cypress_ca42v2_device&#8217;)
/usr/src/modules/cypress_m8.c:256: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:256: warning: (near initialization for &#8216;cypress_ca42v2_device&#8217;)
/usr/src/modules/cypress_m8.c:257: error: unknown field &#8216;description&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:257: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:257: warning: (near initialization for &#8216;cypress_ca42v2_device&#8217;)
/usr/src/modules/cypress_m8.c:258: error: unknown field &#8216;usb_driver&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:258: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:258: warning: (near initialization for &#8216;cypress_ca42v2_device&#8217;)
/usr/src/modules/cypress_m8.c:259: error: unknown field &#8216;id_table&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:259: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:259: warning: (near initialization for &#8216;cypress_ca42v2_device&#8217;)
/usr/src/modules/cypress_m8.c:260: error: unknown field &#8216;num_interrupt_in&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:260: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:260: warning: (near initialization for &#8216;cypress_ca42v2_device&#8217;)
/usr/src/modules/cypress_m8.c:261: error: unknown field &#8216;num_interrupt_out&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:261: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:261: warning: (near initialization for &#8216;cypress_ca42v2_device&#8217;)
/usr/src/modules/cypress_m8.c:262: error: unknown field &#8216;num_bulk_in&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:262: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:262: warning: (near initialization for &#8216;cypress_ca42v2_device&#8217;)
/usr/src/modules/cypress_m8.c:263: error: unknown field &#8216;num_bulk_out&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:263: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:263: warning: (near initialization for &#8216;cypress_ca42v2_device&#8217;)
/usr/src/modules/cypress_m8.c:264: error: unknown field &#8216;num_ports&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:264: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:264: warning: (near initialization for &#8216;cypress_ca42v2_device&#8217;)
/usr/src/modules/cypress_m8.c:265: error: unknown field &#8216;attach&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:265: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:265: warning: (near initialization for &#8216;cypress_ca42v2_device&#8217;)
/usr/src/modules/cypress_m8.c:266: error: unknown field &#8216;shutdown&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:266: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:266: warning: (near initialization for &#8216;cypress_ca42v2_device&#8217;)
/usr/src/modules/cypress_m8.c:267: error: unknown field &#8216;open&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:267: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:267: warning: (near initialization for &#8216;cypress_ca42v2_device&#8217;)
/usr/src/modules/cypress_m8.c:268: error: unknown field &#8216;close&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:268: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:268: warning: (near initialization for &#8216;cypress_ca42v2_device&#8217;)
/usr/src/modules/cypress_m8.c:269: error: unknown field &#8216;write&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:269: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:269: warning: (near initialization for &#8216;cypress_ca42v2_device&#8217;)
/usr/src/modules/cypress_m8.c:270: error: unknown field &#8216;write_room&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:270: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:270: warning: (near initialization for &#8216;cypress_ca42v2_device&#8217;)
/usr/src/modules/cypress_m8.c:271: error: unknown field &#8216;ioctl&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:271: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:271: warning: (near initialization for &#8216;cypress_ca42v2_device&#8217;)
/usr/src/modules/cypress_m8.c:272: error: unknown field &#8216;set_termios&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:272: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:272: warning: (near initialization for &#8216;cypress_ca42v2_device&#8217;)
/usr/src/modules/cypress_m8.c:273: error: unknown field &#8216;tiocmget&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:273: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:273: warning: (near initialization for &#8216;cypress_ca42v2_device&#8217;)
/usr/src/modules/cypress_m8.c:274: error: unknown field &#8216;tiocmset&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:274: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:274: warning: (near initialization for &#8216;cypress_ca42v2_device&#8217;)
/usr/src/modules/cypress_m8.c:275: error: unknown field &#8216;chars_in_buffer&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:275: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:275: warning: (near initialization for &#8216;cypress_ca42v2_device&#8217;)
/usr/src/modules/cypress_m8.c:276: error: unknown field &#8216;throttle&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:276: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:276: warning: (near initialization for &#8216;cypress_ca42v2_device&#8217;)
/usr/src/modules/cypress_m8.c:277: error: unknown field &#8216;unthrottle&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:277: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:277: warning: (near initialization for &#8216;cypress_ca42v2_device&#8217;)
/usr/src/modules/cypress_m8.c:278: error: unknown field &#8216;read_int_callback&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:278: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:278: warning: (near initialization for &#8216;cypress_ca42v2_device&#8217;)
/usr/src/modules/cypress_m8.c:279: error: unknown field &#8216;write_int_callback&#8217; specified in initializer
/usr/src/modules/cypress_m8.c:279: warning: excess elements in struct initializer
/usr/src/modules/cypress_m8.c:279: warning: (near initialization for &#8216;cypress_ca42v2_device&#8217;)
/usr/src/modules/cypress_m8.c:289: warning: &#8216;struct usb_serial_port&#8217; declared inside parameter list
/usr/src/modules/cypress_m8.c: In function &#8216;cypress_serial_control&#8217;:
/usr/src/modules/cypress_m8.c:298: warning: implicit declaration of function &#8216;usb_get_serial_port_data&#8217;
/usr/src/modules/cypress_m8.c:298: warning: assignment makes pointer from integer without a cast
/usr/src/modules/cypress_m8.c:373: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:373: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:384: warning: passing argument 1 of &#8216;cypress_set_dead&#8217; from incompatible pointer type
/usr/src/modules/cypress_m8.c:399: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:399: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:410: warning: passing argument 1 of &#8216;cypress_set_dead&#8217; from incompatible pointer type
/usr/src/modules/cypress_m8.c: At top level:
/usr/src/modules/cypress_m8.c:432: warning: &#8216;struct usb_serial_port&#8217; declared inside parameter list
/usr/src/modules/cypress_m8.c:433: error: conflicting types for &#8216;cypress_set_dead&#8217;
/usr/src/modules/cypress_m8.c:176: error: previous declaration of &#8216;cypress_set_dead&#8217; was here
/usr/src/modules/cypress_m8.c: In function &#8216;cypress_set_dead&#8217;:
/usr/src/modules/cypress_m8.c:434: warning: initialization makes pointer from integer without a cast
/usr/src/modules/cypress_m8.c:445: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c: At top level:
/usr/src/modules/cypress_m8.c:500: warning: &#8216;struct usb_serial&#8217; declared inside parameter list
/usr/src/modules/cypress_m8.c: In function &#8216;generic_startup&#8217;:
/usr/src/modules/cypress_m8.c:503: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:520: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:533: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:534: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:539: warning: implicit declaration of function &#8216;usb_set_serial_port_data&#8217;
/usr/src/modules/cypress_m8.c: At top level:
/usr/src/modules/cypress_m8.c:545: warning: &#8216;struct usb_serial&#8217; declared inside parameter list
/usr/src/modules/cypress_m8.c:546: error: conflicting types for &#8216;cypress_earthmate_startup&#8217;
/usr/src/modules/cypress_m8.c:160: error: previous declaration of &#8216;cypress_earthmate_startup&#8217; was here
/usr/src/modules/cypress_m8.c: In function &#8216;cypress_earthmate_startup&#8217;:
/usr/src/modules/cypress_m8.c:551: warning: passing argument 1 of &#8216;generic_startup&#8217; from incompatible pointer type
/usr/src/modules/cypress_m8.c:557: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:557: warning: assignment makes pointer from integer without a cast
/usr/src/modules/cypress_m8.c: At top level:
/usr/src/modules/cypress_m8.c:564: warning: &#8216;struct usb_serial&#8217; declared inside parameter list
/usr/src/modules/cypress_m8.c:565: error: conflicting types for &#8216;cypress_hidcom_startup&#8217;
/usr/src/modules/cypress_m8.c:161: error: previous declaration of &#8216;cypress_hidcom_startup&#8217; was here
/usr/src/modules/cypress_m8.c: In function &#8216;cypress_hidcom_startup&#8217;:
/usr/src/modules/cypress_m8.c:570: warning: passing argument 1 of &#8216;generic_startup&#8217; from incompatible pointer type
/usr/src/modules/cypress_m8.c:576: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:576: warning: assignment makes pointer from integer without a cast
/usr/src/modules/cypress_m8.c: At top level:
/usr/src/modules/cypress_m8.c:583: warning: &#8216;struct usb_serial&#8217; declared inside parameter list
/usr/src/modules/cypress_m8.c:584: error: conflicting types for &#8216;cypress_ca42v2_startup&#8217;
/usr/src/modules/cypress_m8.c:162: error: previous declaration of &#8216;cypress_ca42v2_startup&#8217; was here
/usr/src/modules/cypress_m8.c: In function &#8216;cypress_ca42v2_startup&#8217;:
/usr/src/modules/cypress_m8.c:589: warning: passing argument 1 of &#8216;generic_startup&#8217; from incompatible pointer type
/usr/src/modules/cypress_m8.c:595: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:595: warning: assignment makes pointer from integer without a cast
/usr/src/modules/cypress_m8.c: At top level:
/usr/src/modules/cypress_m8.c:602: warning: &#8216;struct usb_serial&#8217; declared inside parameter list
/usr/src/modules/cypress_m8.c:603: error: conflicting types for &#8216;cypress_shutdown&#8217;
/usr/src/modules/cypress_m8.c:163: error: previous declaration of &#8216;cypress_shutdown&#8217; was here
/usr/src/modules/cypress_m8.c: In function &#8216;cypress_shutdown&#8217;:
/usr/src/modules/cypress_m8.c:610: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:610: warning: assignment makes pointer from integer without a cast
/usr/src/modules/cypress_m8.c:615: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c: At top level:
/usr/src/modules/cypress_m8.c:620: warning: &#8216;struct usb_serial_port&#8217; declared inside parameter list
/usr/src/modules/cypress_m8.c:621: error: conflicting types for &#8216;cypress_open&#8217;
/usr/src/modules/cypress_m8.c:164: error: previous declaration of &#8216;cypress_open&#8217; was here
/usr/src/modules/cypress_m8.c: In function &#8216;cypress_open&#8217;:
/usr/src/modules/cypress_m8.c:622: warning: initialization makes pointer from integer without a cast
/usr/src/modules/cypress_m8.c:623: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:633: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:634: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:645: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:652: warning: passing argument 1 of &#8216;cypress_write&#8217; from incompatible pointer type
/usr/src/modules/cypress_m8.c:655: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:655: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:655: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:660: warning: passing argument 1 of &#8216;cypress_set_termios&#8217; from incompatible pointer type
/usr/src/modules/cypress_m8.c:663: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:668: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:668: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:669: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:669: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:670: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:670: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:671: warning: passing argument 6 of &#8216;usb_fill_int_urb&#8217; from incompatible pointer type
/usr/src/modules/cypress_m8.c:672: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:675: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:675: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:675: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:676: warning: passing argument 1 of &#8216;cypress_set_dead&#8217; from incompatible pointer type
/usr/src/modules/cypress_m8.c: At top level:
/usr/src/modules/cypress_m8.c:683: warning: &#8216;struct usb_serial_port&#8217; declared inside parameter list
/usr/src/modules/cypress_m8.c:684: error: conflicting types for &#8216;cypress_close&#8217;
/usr/src/modules/cypress_m8.c:165: error: previous declaration of &#8216;cypress_close&#8217; was here
/usr/src/modules/cypress_m8.c: In function &#8216;cypress_close&#8217;:
/usr/src/modules/cypress_m8.c:685: warning: initialization makes pointer from integer without a cast
/usr/src/modules/cypress_m8.c:697: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:703: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:710: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:716: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:717: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:718: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:722: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:730: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:731: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:733: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:734: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:737: warning: assignment makes pointer from integer without a cast
/usr/src/modules/cypress_m8.c:742: warning: passing argument 1 of &#8216;cypress_write&#8217; from incompatible pointer type
/usr/src/modules/cypress_m8.c:747: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:747: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:747: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:749: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c: At top level:
/usr/src/modules/cypress_m8.c:753: warning: &#8216;struct usb_serial_port&#8217; declared inside parameter list
/usr/src/modules/cypress_m8.c:754: error: conflicting types for &#8216;cypress_write&#8217;
/usr/src/modules/cypress_m8.c:166: error: previous declaration of &#8216;cypress_write&#8217; was here
/usr/src/modules/cypress_m8.c: In function &#8216;cypress_write&#8217;:
/usr/src/modules/cypress_m8.c:755: warning: initialization makes pointer from integer without a cast
/usr/src/modules/cypress_m8.c:776: warning: passing argument 1 of &#8216;cypress_send&#8217; from incompatible pointer type
/usr/src/modules/cypress_m8.c: At top level:
/usr/src/modules/cypress_m8.c:782: warning: &#8216;struct usb_serial_port&#8217; declared inside parameter list
/usr/src/modules/cypress_m8.c:783: error: conflicting types for &#8216;cypress_send&#8217;
/usr/src/modules/cypress_m8.c:167: error: previous declaration of &#8216;cypress_send&#8217; was here
/usr/src/modules/cypress_m8.c: In function &#8216;cypress_send&#8217;:
/usr/src/modules/cypress_m8.c:785: warning: initialization makes pointer from integer without a cast
/usr/src/modules/cypress_m8.c:803: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:803: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:803: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:803: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:803: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:803: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:803: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:803: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:803: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:803: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:806: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:810: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:815: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:834: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:835: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:841: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:843: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:846: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:859: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:861: warning: implicit declaration of function &#8216;usb_serial_debug_data&#8217;
/usr/src/modules/cypress_m8.c:861: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:861: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:862: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:864: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:864: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:865: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:865: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:866: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:866: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:867: warning: passing argument 6 of &#8216;usb_fill_int_urb&#8217; from incompatible pointer type
/usr/src/modules/cypress_m8.c:868: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:870: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:870: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:870: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:873: warning: passing argument 1 of &#8216;cypress_set_dead&#8217; from incompatible pointer type
/usr/src/modules/cypress_m8.c:883: warning: implicit declaration of function &#8216;usb_serial_port_softint&#8217;
/usr/src/modules/cypress_m8.c: At top level:
/usr/src/modules/cypress_m8.c:888: warning: &#8216;struct usb_serial_port&#8217; declared inside parameter list
/usr/src/modules/cypress_m8.c:889: error: conflicting types for &#8216;cypress_write_room&#8217;
/usr/src/modules/cypress_m8.c:168: error: previous declaration of &#8216;cypress_write_room&#8217; was here
/usr/src/modules/cypress_m8.c: In function &#8216;cypress_write_room&#8217;:
/usr/src/modules/cypress_m8.c:890: warning: initialization makes pointer from integer without a cast
/usr/src/modules/cypress_m8.c: At top level:
/usr/src/modules/cypress_m8.c:905: warning: &#8216;struct usb_serial_port&#8217; declared inside parameter list
/usr/src/modules/cypress_m8.c:906: error: conflicting types for &#8216;cypress_tiocmget&#8217;
/usr/src/modules/cypress_m8.c:171: error: previous declaration of &#8216;cypress_tiocmget&#8217; was here
/usr/src/modules/cypress_m8.c: In function &#8216;cypress_tiocmget&#8217;:
/usr/src/modules/cypress_m8.c:907: warning: initialization makes pointer from integer without a cast
/usr/src/modules/cypress_m8.c: At top level:
/usr/src/modules/cypress_m8.c:933: warning: &#8216;struct usb_serial_port&#8217; declared inside parameter list
/usr/src/modules/cypress_m8.c:934: error: conflicting types for &#8216;cypress_tiocmset&#8217;
/usr/src/modules/cypress_m8.c:172: error: previous declaration of &#8216;cypress_tiocmset&#8217; was here
/usr/src/modules/cypress_m8.c: In function &#8216;cypress_tiocmset&#8217;:
/usr/src/modules/cypress_m8.c:935: warning: initialization makes pointer from integer without a cast
/usr/src/modules/cypress_m8.c:952: warning: passing argument 1 of &#8216;cypress_write&#8217; from incompatible pointer type
/usr/src/modules/cypress_m8.c: At top level:
/usr/src/modules/cypress_m8.c:956: warning: &#8216;struct usb_serial_port&#8217; declared inside parameter list
/usr/src/modules/cypress_m8.c:957: error: conflicting types for &#8216;cypress_ioctl&#8217;
/usr/src/modules/cypress_m8.c:169: error: previous declaration of &#8216;cypress_ioctl&#8217; was here
/usr/src/modules/cypress_m8.c: In function &#8216;cypress_ioctl&#8217;:
/usr/src/modules/cypress_m8.c:958: warning: initialization makes pointer from integer without a cast
/usr/src/modules/cypress_m8.c:964: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:964: error: invalid application of &#8216;sizeof&#8217; to incomplete type &#8216;struct ktermios&#8217; 
/usr/src/modules/cypress_m8.c:970: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:970: error: invalid application of &#8216;sizeof&#8217; to incomplete type &#8216;struct ktermios&#8217; 
/usr/src/modules/cypress_m8.c:974: warning: passing argument 1 of &#8216;cypress_set_termios&#8217; from incompatible pointer type
/usr/src/modules/cypress_m8.c: At top level:
/usr/src/modules/cypress_m8.c:1019: warning: &#8216;struct usb_serial_port&#8217; declared inside parameter list
/usr/src/modules/cypress_m8.c:1020: error: conflicting types for &#8216;cypress_set_termios&#8217;
/usr/src/modules/cypress_m8.c:170: error: previous declaration of &#8216;cypress_set_termios&#8217; was here
/usr/src/modules/cypress_m8.c: In function &#8216;cypress_set_termios&#8217;:
/usr/src/modules/cypress_m8.c:1021: warning: initialization makes pointer from integer without a cast
/usr/src/modules/cypress_m8.c:1031: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:1061: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:1062: warning: implicit declaration of function &#8216;RELEVANT_IFLAG&#8217;
/usr/src/modules/cypress_m8.c:1063: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:1165: warning: passing argument 1 of &#8216;cypress_serial_control&#8217; from incompatible pointer type
/usr/src/modules/cypress_m8.c:1170: warning: passing argument 1 of &#8216;cypress_serial_control&#8217; from incompatible pointer type
/usr/src/modules/cypress_m8.c:1210: warning: passing argument 1 of &#8216;cypress_write&#8217; from incompatible pointer type
/usr/src/modules/cypress_m8.c: At top level:
/usr/src/modules/cypress_m8.c:1216: warning: &#8216;struct usb_serial_port&#8217; declared inside parameter list
/usr/src/modules/cypress_m8.c:1217: error: conflicting types for &#8216;cypress_chars_in_buffer&#8217;
/usr/src/modules/cypress_m8.c:173: error: previous declaration of &#8216;cypress_chars_in_buffer&#8217; was here
/usr/src/modules/cypress_m8.c: In function &#8216;cypress_chars_in_buffer&#8217;:
/usr/src/modules/cypress_m8.c:1218: warning: initialization makes pointer from integer without a cast
/usr/src/modules/cypress_m8.c: At top level:
/usr/src/modules/cypress_m8.c:1233: warning: &#8216;struct usb_serial_port&#8217; declared inside parameter list
/usr/src/modules/cypress_m8.c:1234: error: conflicting types for &#8216;cypress_throttle&#8217;
/usr/src/modules/cypress_m8.c:174: error: previous declaration of &#8216;cypress_throttle&#8217; was here
/usr/src/modules/cypress_m8.c: In function &#8216;cypress_throttle&#8217;:
/usr/src/modules/cypress_m8.c:1235: warning: initialization makes pointer from integer without a cast
/usr/src/modules/cypress_m8.c: At top level:
/usr/src/modules/cypress_m8.c:1246: warning: &#8216;struct usb_serial_port&#8217; declared inside parameter list
/usr/src/modules/cypress_m8.c:1247: error: conflicting types for &#8216;cypress_unthrottle&#8217;
/usr/src/modules/cypress_m8.c:175: error: previous declaration of &#8216;cypress_unthrottle&#8217; was here
/usr/src/modules/cypress_m8.c: In function &#8216;cypress_unthrottle&#8217;:
/usr/src/modules/cypress_m8.c:1248: warning: initialization makes pointer from integer without a cast
/usr/src/modules/cypress_m8.c:1263: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:1263: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:1265: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:1267: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:1267: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:1267: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:1269: warning: passing argument 1 of &#8216;cypress_set_dead&#8217; from incompatible pointer type
/usr/src/modules/cypress_m8.c: In function &#8216;cypress_read_int_callback&#8217;:
/usr/src/modules/cypress_m8.c:1278: warning: initialization makes pointer from integer without a cast
/usr/src/modules/cypress_m8.c:1300: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:1306: warning: passing argument 1 of &#8216;cypress_set_dead&#8217; from incompatible pointer type
/usr/src/modules/cypress_m8.c:1319: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:1351: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:1395: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:1407: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:1408: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:1408: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:1409: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:1409: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:1411: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:1412: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:1413: warning: passing argument 6 of &#8216;usb_fill_int_urb&#8217; from incompatible pointer type
/usr/src/modules/cypress_m8.c:1414: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:1419: warning: passing argument 1 of &#8216;cypress_set_dead&#8217; from incompatible pointer type
/usr/src/modules/cypress_m8.c: In function &#8216;cypress_write_int_callback&#8217;:
/usr/src/modules/cypress_m8.c:1430: warning: initialization makes pointer from integer without a cast
/usr/src/modules/cypress_m8.c:1451: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:1455: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:1456: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:1456: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:1457: error: dereferencing pointer to incomplete type
/usr/src/modules/cypress_m8.c:1462: warning: passing argument 1 of &#8216;cypress_set_dead&#8217; from incompatible pointer type
/usr/src/modules/cypress_m8.c:1467: warning: passing argument 1 of &#8216;cypress_set_dead&#8217; from incompatible pointer type
/usr/src/modules/cypress_m8.c:1474: warning: passing argument 1 of &#8216;cypress_send&#8217; from incompatible pointer type
/usr/src/modules/cypress_m8.c: In function &#8216;cypress_init&#8217;:
/usr/src/modules/cypress_m8.c:1673: warning: implicit declaration of function &#8216;usb_serial_register&#8217;
/usr/src/modules/cypress_m8.c:1690: warning: implicit declaration of function &#8216;usb_serial_deregister&#8217;
/usr/src/modules/cypress_m8.c:1724:60: warning: no newline at end of file
make[2]: *** [/usr/src/modules/cypress_m8.o] Error 1
make[1]: *** [_module_/usr/src/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-server'
make: *** [all] Error 2



```

---

### Post by aka_bigred on 2009-09-18
> **warp99 said:**
> Since it's just a UPS module I don't think that would be a problem. You may lose some features by doing this, but at least it would work. 


The problem is the communicating with UPS at all.  It's an Ultra Products 1000VA (which is actually a re-bagged PowerCom UPS.  The board ultimately communicates over a serial line, but they put a Cypress Serial-to-USB chip right on the board to cheat and make it a USB device.  The cypress_M8 module on my system doesn't support this device:

lsusb output:
> Bus 002 Device 004: ID 0d9f:0002 Powercom Co., Ltd

So either I need the new cypress_M8 module driver to compile, or the custom powercom_USB module someone wrote for it.  Both are coded to recognize the USB-to-Serial converter and setup a dev/ttyUSB0 device.  Of course, neither will compile on my server and end up with aprox the same failure output I posted above.

---

### Post by Whiffle on 2009-09-18
Yikes, thats some pretty nasty error there on that compile.  I'd suspect that maybe the version of the module you're compiling is incompatable with that kernel.  You might try finding an older version and see if that compiles.

---

