---
title: "Mythtv + suspend-to-ram + resume problem"
date: 2006-05-07
forum: General Help
---

### Post by Vies1 on 2006-05-07
Hi everyone.

I just (finally) build my HTPC on a ubuntu + mythtv platform. No I have finally got it almost working, just few little details.

I would like to get suspend-to-ram work. If I just initiate sleep, and try to resume, everything comes up nicely, but when I try to watch tv, screen remains blank.

Then I tried to stop alsa, mythbackend, mysql and mythfrontend and then initiate sleep. After resume, I start all of those again, but now mythfrontend can't connect to backend.

The backend is running ok, tunned to my tv channels, but somehow frontend can't connect.
mythfrontend tries to find backend from 127.0.0.1:6543 (default in mythtv) and normally it workes, but not after resume.
Maybe there is some problems with looppack device, maybe it dosent resume correctly. I have no idea though.

If anyone have any ideas or suggestion, they would be extremely helpful.
If you guys need any logs or some additional information, I will supply them as soon as possible.

Thank you.

Vies

---

