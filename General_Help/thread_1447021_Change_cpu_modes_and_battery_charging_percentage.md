---
title: "Change cpu modes and battery charging percentage"
date: 2010-04-04
forum: General Help
---

### Post by alphageek89 on 2010-04-04
Is there a way I can specify at what percentage i can make my battery to start charging? I guess the default it 95% which ends up wasting a lot of battery cycles.

And my second question being can i have different modes like power saver,performance?

---

### Post by mickObrian on 2010-04-04
Hmm, I'm not sure about the battery, I run Ubuntu on a desktop. But you can easily set power modes by adding a frequency monitor to the panel, simply right click on the top panel, "Add to panel...", select "CPU Frquency Scaling Monitor" and select add. You can change modes by clicking on the newly added icon on the panel.

---

### Post by 3rdalbum on 2010-04-04
> **alphageek89 said:**
> Is there a way I can specify at what percentage i can make my battery to start charging? I guess the default it 95% which ends up wasting a lot of battery cycles.

I don't think that's how batteries work these days. I might be wrong, but I do know there are a lot of misconceptions about batteries.

> And my second question being can i have different modes like power saver,performance?

You can, but Intel's research shows that the default OnDemand governor is the best mode for power saving (and almost as good for performance), because it allows the CPU to be scaled up to complete a task as quickly as possible, so it can rest for longer. This uses less battery power than having the CPU working hard for a long time at low speed.

---

### Post by alphageek89 on 2010-04-05
since it starts charging when i dips below 95% there must be a file specifying that right? If we know that then I can manually change it i guess.

---

