---
title: "Video card detection at startup causing unity to fail"
date: 2011-05-28
forum: General Help
---

### Post by NPV1597 on 2011-05-28
Hi,
I am trying to get Ubuntu 11.04 fully functioning on my lenovo T500.

The T500 has got two different video cards. An integrated intel one and a high performance ATI one.

I installed with the Intel one, everything was working great.

I switched to the ATI card booted it up and installed the latest fglrx drivers. Again, all is well.

Next, I set up a script to detect which card I am using at boot and select the appropriate driver using this guide:

[http://www.thinkwiki.org/wiki/Auto_detect_drivers_for_switchable_graphics](http://www.thinkwiki.org/wiki/Auto_detect_drivers_for_switchable_graphics)

When I boot with my intel card I get an error message saying my laptop doesn't meet the requirements to use unity.

I ran the unity_support_test and got a segfault.

When I boot with the ATI drivers everything is working great.

Anyone have any idea what else I could add to that script to get unity working on my intel card too?

---

