---
title: "ubuntu does not boot (intel ips failed to get i915 symbols)"
date: 2011-01-18
forum: General Help
---

### Post by olegio on 2011-01-18
My laptop worked fine with Ubuntu 10.10 until this morning. It got frozen while loading desktop icons and since then I can not boot. 
Regular and Recovery boot modes both produce the following and freeze:
[ 12.040952] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled.

Additionally, I can not run Ubuntu from live cd, it freezes while showing Ubuntu logo on startup.

Everything worked fine until now. I have a dual boot and Windows 7 works perfectly.
Any idea how to approach this, since I can't even reinstall Ubuntu.

---

### Post by lithopsian on 2011-01-18
Duplicate

---

### Post by lithopsian on 2011-01-18
There are known problems related to Intel IPS where errors are reported that seem to be fictitious.  Try blacklisting the intel-ips module.  You probably don't want to leave it that way, but it might get you booted.

I would expect booting to the command line should work.  If not then you really might have a hardware problem.  Can you access the modprobe configuration files from Windows?

---

### Post by olegio on 2011-01-18
> **lithopsian said:**
> There are known problems related to Intel IPS where errors are reported that seem to be fictitious.  Try blacklisting the intel-ips module.  You probably don't want to leave it that way, but it might get you booted.

I would expect booting to the command line should work.  If not then you really might have a hardware problem.  Can you access the modprobe configuration files from Windows?

After blacklisting the intel-ips, the "ips failed" messgae disappeared, but the boot still hangs at:

Begin: Running /scripts/init-bottom ... done

Maybe, the actual problem is there and does not have anything to do with intel-ips. 

If it is a hardware problem, then it only affected ubuntu, because Windows 7 runs without any problem.  

I was able to run Ubuntu 9.04 from Live CD, (10.04, 10.10 do not load).
Ubuntu 10.10 from live cd hangs after the same line:
Begin: Running /scripts/init-bottom ... done

---

