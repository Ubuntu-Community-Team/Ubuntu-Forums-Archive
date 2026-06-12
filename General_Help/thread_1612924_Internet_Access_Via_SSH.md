---
title: "Internet Access Via SSH"
date: 2010-11-03
forum: General Help
---

### Post by tekkidd on 2010-11-03
Hi, on one of my networks due to a  firewall conflict i cannot access the Internet on my laptop, i have another computer that can access the Internet and i have SSH access to the box. My question is how i would set it up so i could access the Internet through that SSH connection

---

### Post by marshmallow1304 on 2010-11-04
I use dynamic port forwarding, like so

```
ssh [user@]host -D 8080
```

Of course, you can use a different port if you wish.

Now set up your browser to use a Socksv5 proxy pointed to
localhost 8080

In Firefox, this is under Edit->Preferences->Advanced->Network->Settings...
System->Preferences->Network Proxy might work too, but I don't know as I've never bothered with it.

---

### Post by tekkidd on 2010-11-04
thanks

---

