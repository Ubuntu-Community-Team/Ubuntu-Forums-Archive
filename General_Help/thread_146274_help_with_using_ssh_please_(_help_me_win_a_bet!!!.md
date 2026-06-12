---
title: "help with using ssh please :( help me win a bet!!!"
date: 2006-03-18
forum: General Help
---

### Post by shooshu on 2006-03-18
[COLOR="Red"][FONT="Courier New"]hey, i am interested in learning how to connect to someones firewall via ssh, then connect to a computer via ssh, then setup a ssh tunnel and vnc can anybody help me please. by the way i do have permission to connect to their firewall, im trying to win a bet. he reconds that because im a girl who uses linux i wont be able to do it- so far, im failing. lol :(:([/FONT][/COLOR]

---

### Post by bjweeks on 2006-03-18
Hack him?

---

### Post by tkiesel on 2006-03-18
You won't connect to the firewall itself.

There'll need to be an open port on the firewall. That port will have to be forwarded to the port that ssh is listening to on your friend's machine.

Basically your friend needs to invite you in by setting all of that up.

Once your friend has all of that arranged, all you have to do is...

```
ssh -p port# username@firewall_IP#
```

Your part is the easy part. I'm surprised that he thinks you won't be able to do that because you're female.  Seems like he's something of a misogynist.

---

### Post by dasunst3r on 2006-03-18
I'm cheering for you, shooshu!  I really want to see that gender barrier taken down (this is coming from a guy, btw).

If he has the computer firewalled and port 22 unopened, then there's pretty much no way of getting in.

---

### Post by JimShoe on 2006-03-28
```
ssh -ND port user@host
ssh -fND port user@host
```

this makes the tunnel dynamic, and turns it into a socks5 proxy, with setting as "127.0.0.1: port" this way you can run anything that cause use a socks 5 proxy.  Also the "-f" makes that session run in the background.

---

