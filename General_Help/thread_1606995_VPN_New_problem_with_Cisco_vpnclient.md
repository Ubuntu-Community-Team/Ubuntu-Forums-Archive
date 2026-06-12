---
title: "VPN: New problem with Cisco vpnclient"
date: 2010-10-27
forum: General Help
---

### Post by bigblackcar on 2010-10-27
I have installed the Cisco vpnclient to connect to a VPN. Standard Ubuntu VPN connection would not work.

The connection has worked fine for > 1 year, apart from the fact that I was force to reinstall it with every kernel update.

Now it doesn't work anymore. When I run:

```
sudo vpnclient connect hc-vpn &
```

I receive the following error message:

```
Copyright (C) 1998-2007 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.32-25-generic #45-Ubuntu SMP Sat Oct 16 19:52:42 UTC 2010 x86_64
Config file directory: /etc/opt/cisco-vpnclient

Enter a group password: tcsetattr error: Interrupted system call
tcsetattr error: Interrupted system call

```

Anybody has any idea on how to make it work?

Thanks in advance.

---

### Post by clrg on 2010-11-07
I use the same kernel, but when I try to connect, my system locks up completely (kernel panic) and I have to force a power cycle.

Any help would be greatly appreciated, since I need VPN to be able to work from home. VPNC is not an option, since it doesn't support concentrator compression, which my company has enabled.

---

