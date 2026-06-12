---
title: "X over telnet"
date: 2012-02-04
forum: General Help
---

### Post by conradin on 2012-02-04
Hi all, 
I want to use X over a telnet connection. The Host is Running IRIX 5.2 and the client is running IRIX 6.5. Im trying to pull this off via the command line, any help would be greatly appreciated. Neither machine has ssh.

---

### Post by haqking on 2012-02-04
> **conradin said:**
> Hi all, 
I want to use X over a telnet connection. The Host is Running IRIX 5.2 and the client is running IRIX 6.5. Im trying to pull this off via the command line, any help would be greatly appreciated. Neither machine has ssh.

mmm its been a while, im not in ubuntu right now.

But unless things have changed you cant forward X over telnet (and telnet is extremely insecure so be warned)

however you can use setenv to point back to your local X server i think but i cant remember how its done....LOL

once your connected via telnet (presuming Xserver is listening on a given port)

you use the setenv command but i dont think its supported in Ubuntu.

I will look into it and post back unless someone else chimes in.

---

### Post by Dangertux on 2012-02-04
So long as tcp connection to xserver is allowed you can do it from within your telnet session by doing the following. Your xserver has to be listening for incoming connections.

```

xeyes -display localhostip:0.0

```Should do it.

Or maybe.. on remote machien
```

setenv DISPLAY yourip:0.0

```

I think... I haven't done this in forever you might have to play with it and read the x server manual but yes it can be done.

---

### Post by haqking on 2012-02-04
> **Dangertux said:**
> So long as tcp connection to xserver is allowed you can do it from within your telnet session by doing the following. Your xserver has to be listening for incoming connections.

```

xeyes -display localhostip:0.0

```Should do it.

Or maybe.. on remote machien
```

setenv DISPLAY yourip:0.0

```

I think... I haven't done this in forever you might have to play with it and read the x server manual but yes it can be done.

ha ha yeah that sounds about right, you were like me, been ages since i did that.

Think that will do the trick though

---

