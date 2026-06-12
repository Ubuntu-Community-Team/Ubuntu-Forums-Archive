---
title: "How to do voip with console/server with OHPHONE? (config)"
date: 2009-09-20
forum: General Help
---

### Post by frenchn00b on 2009-09-20
Hello

OHPHONE will help geeks, that use console instead of X.
Any ideas how to configure it, to do calls with alsa + video?:popcorn::popcorn:
#
should we tunnel it trhough SSH ? which port , 7000?

---

### Post by frenchn00b on 2009-09-20
ok 
port 1720

apt-get install ohphone

SERVER LISTENING:
```
ohphone -ln
```
it has ip 192.169.0.100


CLIENT:
```
ohphone -n 192.169.0.100
```

the server does Yes !! it works!!
Simple

[B][COLOR="Magenta"]Questions:
1/ how can ekiga windows call to OHPHONE?? 
```
sip:192.169.0.100
```
not working
 
2/ I havent any sound
how to enable USB to use my USB mic[/COLOR][/B]

---

