---
title: "Run program on startup - on twinview"
date: 2010-03-27
forum: General Help
---

### Post by SpritBille on 2010-03-27
Hey.

I have connected my TV (and my regular screen) to my Ubuntu 9.10. I use TwinView, and that works just fine. I have also installed Moovida (I love that program). And I would like my PC to open Moovida on startup, but I need it to be on the TV screen. How do I do that?

Thnaks.

Kind regards Bille

---

### Post by SpritBille on 2010-04-05
Now i got it.

System -> Preferences -> startup applications

In command type; "env DISPLAY=:0.1 moovida"

moovida is the application, and 0.1 means the second monitor (0.0 for the default monitor)

---

