---
title: "Need help choosing a UPS"
date: 2011-07-11
forum: General Help
---

### Post by techningeer on 2011-07-11
Hi everbody,
I was looking for a Uninteruptable Power Supply today, but there is virtually no help on choosing one. I need one that works with Ubuntu and Windows XP. Can you give me some suggestions?

--techningeer

---

### Post by Mark Phelps on 2011-07-11
UPS is hardware and doesn't care about the OS on the PC to which it is connected -- so it will work with ANY OS.

But ... if you're looking for one that has monitoring SW that will work with both, you're most probably NOT going to find one.  I've tried several (mostly by APC), and all of them had Windows-only software.

---

### Post by SeijiSensei on 2011-07-11
Linux has excellent support for an APC UPS via the **apcupsd** package that's in the repositories.  It will monitor the UPS when connected with a USB cable, and, in networked environments, you can set up the other Linux boxes to monitor the power over the network.

The real question is how many devices you need to connect to the UPS and what types of devices they are.  You should probably use a "calculator" like the one [on this page](http://www.apc.com/tools/ups_selector/).  If you're only intending to support a couple of servers and maybe a couple of low-power devices like a wifi router, a UPS [like this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16842101339") would probably be fine.

You shouldn't expect to get more than about 20-30 minutes of battery backup from most UPS's unless you can make a big financial investment.  That's fine for transient loss of power but won't help much if you get hit by a hurricane.

---

