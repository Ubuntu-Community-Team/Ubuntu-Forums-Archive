---
title: "SSH users"
date: 2010-10-20
forum: General Help
---

### Post by baddnady23 on 2010-10-20
I have a desktop (computer 1) set up with open-ssh that I can remotely access using 
```
ssh andrew@9X.XX3.1X.XX0
```
and have no problems doing so. 

I also have another desktop (computer 2) with the same user name (andrew) on the same network, the local address is 162.168.1.70.  My question is how would I specify from a remote location that I want to access computer 2 rather than computer 1?  Both computers have port 22 forwarded for SSH.

---

### Post by Sub101 on 2010-10-20
What I would do is have each pc using a different port for connection. And configure that in your router settings.

---

### Post by luvshines on 2010-10-20
If I get your question correct, you want to connect to 169 machine with andrew user from remote location.

If you are able to access the 169... machine from remote location then ssh andrew@169... should take you to machine 2 and not 1

---

### Post by Baked- on 2010-10-20
If you only have 1 internet IP you can ssh to the one you have 22 forwarded to and use the internal ip to ssh to the other from there

or

set ssh on computer2 to use a non default port and forward that port to computer2

---

### Post by baddnady23 on 2010-10-20
@sub101:

in doing that, then how would I specify when I login which port I want to be directed to?

---

### Post by CharlesA on 2010-10-20
If you forwarded both to a different port on the router, you'd have to connect like so:

```
ssh -p 22 user@host
```

---

### Post by Sub101 on 2010-10-20
> **baddnady23 said:**
> @sub101:

in doing that, then how would I specify when I login which port I want to be directed to?

Simply edit on the router where to send each connection. 

For my router it would mean setting the virtual servers to receive on port *yourchoice* and forward to port 22 on for each IP.

So for example. PC 1 ; forward port 1234 to PC1 port 22
                PC 2 ; forward port 4321 to PC2 port 22

---

