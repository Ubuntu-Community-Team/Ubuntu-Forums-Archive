---
title: "Socket operation on non-socket OLSR"
date: 2010-12-22
forum: General Help
---

### Post by zfima on 2010-12-22
Hello
I am using OLSRD
I face problem. Scenario:

    1. Run olsr_switch
    2. Run olsrd -f /etc/olsrd.emu.conf -hemu 10.0.0.1 -d 1

Get output:
sendto(v4): Socket operation on non-socket
sendto(v4): Socket operation on non-socket
sendto(v4): Socket operation on non-socket
sendto(v4): Socket operation on non-socket
sendto(v4): Socket operation on non-socket
.....

What i need add in olsrd.emu.conf file?
Please, help me

---

### Post by zfima on 2010-12-22
Any information will help me... Only before 1 week i install Ubuntu and it new for me...

---

### Post by WOLFY17 on 2011-02-01
I have the same problem - the program does not go into the host emulation mode, but I tried to edit the source code so that it moved into it, but it did not help ... probably need to add some line in the configuration file
you're having any results?

---

