---
title: "x2x help"
date: 2011-02-09
forum: General Help
---

### Post by Scooter_X on 2011-02-09
Hey guys, I ran across a cool program that I would like to try out called x2x, which for those who don't know allows me to use the keyboard and mouse from one computer on another computer. Just google it and you'll find explanations better than that, but you get the gist?

Anyhow, I've installed SSH server and x2x on the computer that I want to control (laptop) and on the computer that I want to use to control the laptop (workstation) I stuffed into a terminal the following: 
```
ssh -XC riley@riley-Eee  x2x -east -to :0.0
```

which, riley@riley-Eee does in fact refer to the laptop that I want to control. All I get back out is:
```
ssh: Could not resolve hostname riley-Eee: Name or service not known

```

even though both systems are on the same router. I would assume that it should work right away no problem, but it doesn't. I don't understand SSH very well (or networking in general) so I'm wondering if someone knows how to step-by-step me through getting it to work. I'd appreciate it. Thanks.

---

### Post by Scooter_X on 2011-02-09
Dang. I usually post questions but then I wind up solving them on my own. All I had to do was instead of riley@riley-Eee, I put riley@<ip address>. I did ifconfig before, but didn't understand which one was my IP of all the numbers that were scattered across my screen. I found it. It worked. Why did it work with the IP instead of the riley-Eee thing? Feel free to answer, but I'll probably have already looked it up by then. :P

---

