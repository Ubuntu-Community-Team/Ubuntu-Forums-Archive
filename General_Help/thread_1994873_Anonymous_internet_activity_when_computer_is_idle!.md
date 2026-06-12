---
title: "Anonymous internet activity when computer is idle!"
date: 2012-06-03
forum: General Help
---

### Post by Rushyang on 2012-06-03
Bonjour guys,
I am using Ubuntu 10.10 x64. And my problem is, when my computer is idle sometimes I observe some anonymous traffic activity going on! Not in bytes, it downloads and uploads something at the rate of 40-50 kbps and cause I have limited internet data usage(2.5GB/month), I observe sometimes more than 50MB of total data transfer / idle hour! Now this gets on my nerves. I'd be okay with it if I had unlimited internet connection. But I have not!

I googled, and I came up with the package named "EtherApe". Though which all these activity is redirected on some servers based in Canada. (I'm in India and my ISP's international server is in Bangalore, India)
Here are names of those nodes. (as per displayed in EtherApe)

maa03s05-in-f31.1e100.net
maa03s05-in-f22.1e100.net
maa03s05-in-f4.1e100.net

I'm not able to figure out which application/package is sending/receiving those data. Can please someone help me out with this?

---

### Post by LinGNUbie on 2012-06-03
check with network tools > netstat to see which ports are being used. Also some applets in the launcher can be requesting data updates such as time, weather, empathy broadcast. A look into the processes should show what is being used, in terminal enter top OR ps aux.

---

### Post by gschoper on 2012-06-03
1e100.net is owned by Google and used for google services. See [http://support.google.com/bin/answer.py?hl=en&answer=174717]("http://support.google.com/bin/answer.py?hl=en&answer=174717")

---

### Post by sanderj on 2012-06-03
> **gschoper said:**
> 1e100.net is owned by Google and used for google services. See [http://support.google.com/bin/answer.py?hl=en&answer=174717]("http://support.google.com/bin/answer.py?hl=en&answer=174717")

Indeed. Easy to see:

```
sander@R540:~$ netstat -apo | grep 1e100
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
tcp        0      0 R540.home:35587         wb-in-f102.1e100.:https ESTABLISHED 3271/chromium-brows keepalive (14.66/0/0)
tcp        0      0 R540.home:48542         wg-in-f132.1e100.:https ESTABLISHED 3271/chromium-brows keepalive (38.47/0/0)
tcp        0      0 R540.home:42215         wb-in-f19.1e100.n:https ESTABLISHED 3271/chromium-brows keepalive (1.61/0/0)
tcp        0      0 R540.home:35211         wi-in-f120.1e100.:https ESTABLISHED 3271/chromium-brows keepalive (38.47/0/0)
tcp        0      0 R540.home:48654         wi-in-f113.1e100.:https ESTABLISHED 3271/chromium-brows keepalive (2.12/0/0)
tcp        0      0 R540.home:34055         wi-in-f94.1e100.ne:http ESTABLISHED 3271/chromium-brows keepalive (40.91/0/0)
tcp        0      0 R540.home:54146         wi-in-f94.1e100.n:https ESTABLISHED 3271/chromium-brows keepalive (41.29/0/0)
sander@R540:~$

```

So, question to the OP: how idle is your computer? If an account is still logged on and the Chrome webbrowser is open, you cannot call it idle.

So if you want an idle computer, make sure everybody is logged off. And even then, some background processes will run.

If you really want to be sure of zero network traffic, disable the network or unconnect it.

---

