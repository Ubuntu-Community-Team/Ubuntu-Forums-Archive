---
title: "mp3 player won't automount"
date: 2006-04-13
forum: General Help
---

### Post by linuxted on 2006-04-13
This used to work for me and stopped recently.  I've tried rebooting, reloading ipod software (on my Windows machine) and using USB1.0... with no luck.  Anyone else having this problem recently?

Any workarounds?  I want Linux and my ipod nano to play nicely.


Thanks
](*,)

---

### Post by linuxted on 2006-04-14
More info:

unless i do "rmmod ehci_hcd" I cannot even see the player on Ubuntu.

Any ideas?


Thanks

---

### Post by linuxted on 2006-04-14
[QUOTE=linuxted]More info:

unless i do "rmmod ehci_hcd" I cannot even see the player on Ubuntu.

Any ideas?


Thanks[/QUOTE]

and if I don't do the rmmod trick, I get the following with tail /var/log/messages

Apr 13 22:43:46 localhost kernel: [   83.158027] usb 4-7: new high speed USB device using ehci_hcd and address 3

And I can't talk to the ipod at all
please help!

---

