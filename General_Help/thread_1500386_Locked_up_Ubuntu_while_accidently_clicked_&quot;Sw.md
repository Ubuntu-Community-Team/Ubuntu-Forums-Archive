---
title: "Locked up Ubuntu while accidently clicked &quot;Switch user&quot; on VNC login"
date: 2010-06-03
forum: General Help
---

### Post by Zwartejas on 2010-06-03
Hi,

I started a remote VNC connection from my Windows pc to my Ubuntu desktop, got presented with the Ubuntu login screen. Entered my password and accidently clicked the "Switch user" key instead of "Unlock".

The login panel became grey and now I cant do anything (I guess its because there is no other user). When I exit and enter through VNC I allways come back at the same grey screen (see screenshot below).

Is there any way of bypassing this and unlock my ubuntu desktop?

**The problem: (After clicking switch user)**
[IMG]http://upload.halflife-2.nl/20100603-19005.jpg[/IMG]

---

### Post by Zwartejas on 2010-06-03
Nobody?

---

### Post by tankjer on 2010-06-03
> **Zwartejas said:**
> Nobody?
Be a bit more patient. Bump the thread if there's no response for at least a day. If you want immediate support go to some IRC.
On thread: Does anything happen when you use CTRL+ALT+DEL in VNC?

---

### Post by Zwartejas on 2010-06-03
No i have tried CTRL + ALT + DEL but no response. Also send the CTRL + ALT + DEL command manually through the VNC service.

---

### Post by aeiah on 2010-06-03
why dont you just reboot the box? or restart the vnc service? you can do either through ssh
```

sudo reboot

```

```

sudo service vncservicename restart

```

i dont know what your vnc service is called though. you should be able to list all services with
```

service --status-all

```

---

### Post by Iced on 2012-08-18
I know this is a couple year old thread, but I was looking for an answer and nobody has answered this thread so I will post what worked for me.

CTRL-ALT-F8 in the VNC client will restore the login screen

---

