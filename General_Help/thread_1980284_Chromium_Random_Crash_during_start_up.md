---
title: "Chromium Random Crash during start up"
date: 2012-05-14
forum: General Help
---

### Post by iamgeniusrnti on 2012-05-14
Here's the log I get.  But basically sometimes Chromium takes a long time to load and then crashes.  If I restart the program, it will take a long time to load again and then it will work.  Seems random.  Not sure if it's a bug.


```
05/13/12 12:02:00 PM		chromium-browse[14494] trap invalid opcode ip:7fa750fb6aed sp:7fffdfc1e7d8 error:0 in chromium-browser[7fa74e6ca000+4129000]
05/13/12 12:02:05 PM		chromium-browse[15162] trap invalid opcode ip:7fa750fb6aed sp:7fffdfc1e7d8 error:0 in chromium-browser[7fa74e6ca000+4129000]
```

---

### Post by NikoC on 2012-06-04
Same problem here, no solution found yet! Running Kubuntu 12.04 with chromium stable! For now when chromium hangs I open Konsole and kill all chromium processes with:

sudo killall chromium-browse

After doing so, chromium starts up fine...

---

