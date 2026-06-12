---
title: "Apt-get and software centre won't install packages"
date: 2011-10-30
forum: General Help
---

### Post by GCoffee on 2011-10-30
Hi,

apt-get and 'The Ubuntu Software Centre' have suddenly stopped installing packages. Software centre tells me that the download has failed (when the internet connection is fine) while apt-get hangs on:

```

Do you want to continue [Y/n]? y
0% [Connecting to 89.188.141.51 (89.188.141.51)

```

Pinging 89.188.141.51 loses all packets.

This happens regardless whether I set "Main server" or "United Kingdom server" in the software sources dialogue.

Any help on this issue? (IE: connect to a different server or bypass 89.188.141.51?)

Thanks,
GC.

---

### Post by Pithikos on 2011-10-30
> **GCoffee said:**
> Hi,

apt-get and 'The Ubuntu Software Centre' have suddenly stopped installing packages. Software centre tells me that the download has failed (when the internet connection is fine) while apt-get hangs on:

```

Do you want to continue [Y/n]? y
0% [Connecting to 89.188.141.51 (89.188.141.51)

```Pinging 89.188.141.51 loses all packets.

This happens regardless whether I set "Main server" or "United Kingdom server" in the software sources dialogue.

Any help on this issue? (IE: connect to a different server or bypass 89.188.141.51?)

Thanks,
GC.

The server seems down:
```
PING 89.188.141.51 (89.188.141.51) 56(84) bytes of data.
^C
--- 89.188.141.51 ping statistics ---
118 packets transmitted, 0 received, 100% packet loss, time 117003ms
```Start *Software Sources* and then go to Ubuntu Software > Download from > ..
You should be able to choose* Other..* there and get a list with servers. Choose one and then
```
sudo apt-get update
```

---

### Post by GCoffee on 2011-10-30
Will give it a go.

Thanks.

---

### Post by GCoffee on 2011-10-30
Hi,

Regardless of which server I select, I run apt-get update and it still tries to connect to 89.188.141.51, hangs, and fails.

Any advice?

---

