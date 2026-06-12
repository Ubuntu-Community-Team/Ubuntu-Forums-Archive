---
title: "iRecovery install problems"
date: 2011-10-27
forum: General Help
---

### Post by azmatt on 2011-10-27
I'm a 20+ year DOS and Windows vet but linux newbie. I installed 10.04 LT edition and tried to install iRecovery. When running the make linux I get the following error
 
gcc irecovery.c -o irecovery -lusb -lreadline
irecovery.c:22:17: error: usb.h: No such file or directory
irecovery.c: In function ‘irecv_init’:
irecovery.c:48: warning: assignment makes pointer from integer without a cast
irecovery.c:48: error: dereferencing pointer to incomplete type
irecovery.c:49: error: dereferencing pointer to incomplete type
irecovery.c:49: error: dereferencing pointer to incomplete type
irecovery.c:50: error: dereferencing pointer to incomplete type
irecovery.c:50: error: dereferencing pointer to incomplete type
irecovery.c:51: warning: assignment makes pointer from integer without a cast
irecovery.c: In function ‘irecv_console’:
irecovery.c:253: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
irecovery.c: In function ‘irecv_sendcmd’:
irecovery.c:280: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
irecovery.c: In function ‘main’:
irecovery.c:323: error: ‘SIGINT’ undeclared (first use in this function)
irecovery.c:323: error: (Each undeclared identifier is reported only once
irecovery.c:323: error: for each function it appears in.)
make: *** [linux] Error 1
 
It was originally saying it couldnt find readline.h but I got that installed. I've failed in every attempt to get libusb installed for two days. The configure gives me the "lib/cpp" fails sanity check error
 
When I type which cpp it shows /usr/bin/cpp
 
I've spent two days googling and trying to install diffrent things with varying sucess but am beyond frustrated so I thought I would check here.
 
Any help would be greatly appreciated.
 
Thanks,
 
Matt

---

