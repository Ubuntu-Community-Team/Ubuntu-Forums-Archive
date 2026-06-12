---
title: "How to Redirect an Application to Use SOCKS 5??"
date: 2009-07-19
forum: General Help
---

### Post by Laibcoms on 2009-07-19
I've read different manuals and guides and I still can't get it to work, so asking here.

Basically, I have well ssh, and I installed tsocks.

I have my ssh open/running.

I setup my tsocks conf to:
```

local = 192.168.1.254/255.255.255.0
server = 127.0.0.1
server_type = 5
server_port = 1080 

```

My connection/LAN info:
```

Default Route: 192.168.1.254
Primary DNS: 192.168.1.254
Subnet Mask: 255.255.255.0

```

I did (using example WoW) 
1) . tsocks -on
2) run WoW via POL -> tsocks /usr/share/playonlinux/playonlinux --run "WorldOfWarcraft"
3) logged-in
4) I terminated my ssh connection
5) I'm still logged-in to the game - my setup is not working in other words

If I try another app, for example epiphany - no websites will load.
If I don't use tsocks for epiphany, it works fine.

So the more I am confused.  If I use any other app, it "seems" to be working (like epiphany) but if I use WoW, it isn't sockified.

??? T_T ???

I get this error from WoW btw:
```

libtsocks: Unresolved symbol: close
libtsocks: Unresolved symbol: close
PlayOnLinux v3.6

Checking python :                 [ Ok ]
ERROR: ld.so: object '/usr/lib/libtsocks.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libtsocks.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libtsocks.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libtsocks.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libtsocks.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libtsocks.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libtsocks.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libtsocks.so' from LD_PRELOAD cannot be preloaded: ignored.

```

Thanks for any help.

---

### Post by bswilson on 2009-09-24
You're running tsocks 2 times, that's causing the error.  When you've enabled the LD_PRELOAD environment variable, you don't need to also preface your commands with `tsocks`.  Just do this:
```

. tsocks off && tsocks /usr/share/playonlinux/playonlinux --run "WorldOfWarcraft"
```

---

