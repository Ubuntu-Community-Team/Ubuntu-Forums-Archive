---
title: "Joining multiple servers on irssi"
date: 2009-08-17
forum: General Help
---

### Post by j33zU5 on 2009-08-17
Pretty much what the title says. I can't find it anywhere in documentation and when I /server it will just close the current server I have open and join the new one

---

### Post by andrew.46 on 2009-08-18
Hi j33zU5,

> **j33zU5 said:**
> Pretty much what the title says. I can't find it anywhere in documentation and when I /server it will just close the current server I have open and join the new one

irssi should be able to connect to multiple servers at the same time but the command you are after is */connect*. For example:

```
/connect irc.freenode.net 8001
```

The /server command has a slightly different action:

```
/SERVER disconnects the server in active window and connects to the new one.
```

which I suspect pretty much covers your problem :).

Andrew

---

