---
title: "Ethernet Lan not working ?!?"
date: 2010-05-30
forum: General Help
---

### Post by Baffo on 2010-05-30
Hello,

I am booting Ubuntu 10.04 LTS from my usb stick.
I use an Ethernet Cable for connection, but it does not work !

On windows it does not require any configuration (DHCP).

How can i get my cable to work in ubuntu ??
Please help.
:)

---

### Post by Baffo on 2010-05-30
any help please :) ?

---

### Post by sedawk on 2010-05-30
You can try do run
```

ifconfig eth0

```
to see if you got assigned an IP address.

And check the kernel message buffer for anything about eth0:
```

dmesg|grep eth0

```

If the first command doesn't show a proper IP address you
can try to get one via dhcp manually:
```

sudo dhclient eth0

```

---

### Post by Baffo on 2010-05-30
I can ping the router correctly, but i cannot browse the web !

---

### Post by JustinR on 2010-05-30
If you can ping the router but can't access the internet most likely your router isn't connected to the internet.

Make sure your modem is setup correctly and connected to a phone line.

If thats not the case make you your aren't using any proxy settings unless required to.

---

### Post by Baffo on 2010-05-30
Dear JustinR, the router is ok, because on windows i can surf fine.

---

### Post by Baffo on 2010-05-30
any help please?

I have tried to configure different dns servers but it doesnt work either!!

---

### Post by JustinR on 2010-05-30
Okay then. So I guess the simplest way to do this would be to do this:

Can you get a screenshot of the connection information dialogue when you right click the Internet Connection tray icon?

---

### Post by alphacrucis2 on 2010-05-30
Please report back with output from these three commands:


```
ifconfig
cat /etc/resolv.conf
route -n
```

---

### Post by Baffo on 2010-05-30
It says that auto eth0 is connected

---

### Post by alphacrucis2 on 2010-05-30
> **Baffo said:**
> It says that auto eth0 is connected

Need the full output.

---

### Post by bakegoodz on 2010-05-30
I had the similar problem problem once, it through me for a loop for hours. Couldn't be my router since my Mac connected to the internet fine. Turned out the gateway address wasn't set and being given out via dhcp. I think other OS's will take a educated guess if the gateway is not given, but Linux won't.

---

### Post by Baffo on 2010-05-31
I am sorry, so what should i do exactly, bakegoodz ?

---

### Post by Baffo on 2010-05-31
Bump ? :)

---

