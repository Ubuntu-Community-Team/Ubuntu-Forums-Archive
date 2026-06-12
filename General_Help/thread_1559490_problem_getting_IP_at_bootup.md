---
title: "problem getting IP at bootup"
date: 2010-08-23
forum: General Help
---

### Post by Josey on 2010-08-23
So when I boot into ubuntu 10.4 the internet is not working and the 'network manager applet' near shutdown and chat in the taskbar says 'no network connection'

If I open terminal and run 'sudo dhclient eth0' I get an IP address from my router and then I can use the internet as normal.  The network manager applet still claims there is no connection though.

This causes problems in various programs like firefox which keeps assuming it should be in offline mode and various troubles with empathy and other programs that seem to think I don't have a net connection when in fact I do.

I have reset my router and it should be handing me a dhcp address when I boot up.

Any idea on how to fix this?  Thanks in advance.

---

### Post by eric_1982 on 2010-08-23
May not be the best fix but you could just add that command to your start up. 

I would also take a look at your /etc/network/interfaces file and see if anything looks out of the norm.

---

### Post by Josey on 2010-08-23
This is all that is in my interfaces file.

```
auto lo
iface lo inet loopback
```


edit: adding this to my interfaces file fixed it, thank you for pointing me toward that file. :)

```
auto eth0
iface eth0 inet dhcp
```

---

