---
title: "VNC to OS X 10.4?"
date: 2006-03-09
forum: General Help
---

### Post by schnarff on 2006-03-09
Hello All,

I've got a VNC server (or, more accurately, an Apple Remote Desktop) set up on my new MacBook Pro, which is running 10.4.<whatever the latest patch level is>. I had seen elsewhere that I could just use tsclient to connect to it; however, as with all things Linux, it's Just Not That Easy (TM).

Basically, when I fire up tsclient, enter the IP address, user name, and "VNC" as the protocol, I get the following error:

```
VNC server supports protocol version 3.889 (viewer 3.3)
ReadFromRFBServer: rdr::EndOfStream
```

Trying "RDP" or "RDPv5" just gives me a connection refused erorr, which of course is no help.

I went out and tried looking up the error message, and several sites stated that it meant that my VNC client was old and couldn't support the newer protocol understood by the server. That's clearly crap, though, since a) I'm running an up-to-date copy of Breezy Badger here, and b) I went to the tsclient site and found that I've got the latest version.

Does anyone have any idea how to fix this? I'm at a real loss here.

Thanks,
Alex Kirk

PS Probably not relevant, but my client is AMD64. Just throwing that out there on the off-chance that it means something.

---

### Post by aysiu on 2006-03-09
Have you tried *xtightvncviewer*? It's in the standard repositories.

---

### Post by schnarff on 2006-03-09
Not helpful, unfortunately:

```
alex@alex:~$ xtightvncviewer 192.168.1.10
VNC server supports protocol version 3.889 (viewer 3.3)
xtightvncviewer: VNC server closed connection

```

It's almost as if there are underlying VNC libraries that are out of date. Any thoughts on that possibility?

---

### Post by aysiu on 2006-03-09
Maybe you should consider using a different VNC *server*?

Maybe OSXvnc?
[http://sourceforge.net/projects/osxvnc](http://sourceforge.net/projects/osxvnc)

---

