---
title: "CPU fan keeps running"
date: 2011-07-08
forum: General Help
---

### Post by payot on 2011-07-08
After the installation of Ubuntu , my CPU fan keeps running without any breaks. When I switch to Windows XP Pro ,everything looks fine. CPU fan stops after some short time and then starts when my CPU needs it.
Any ideas why Ubuntu keeps the CPU fan cooler running?

Info:
Memory : 4 Gib
Processor : Intel Core 2 Duo CPU 2.8

thanks in advance

---

### Post by FormatSeize on 2011-07-08
Windows has mechanisms in place that shut down certain pieces of hardware that are not in use, (like a wireless card or something like that) while Ubuntu has no such mechanisms. As such, your fan has to do more work to keep the system cool.

---

### Post by Erik1984 on 2011-07-08
It depends on your hardware if fan control works properly in Linux out of the box. On my system the fan adjusts to the CPU usage. So it's not that Ubuntu always has this fan problem, just with some hardware. However all is not lost. I believe there a some boot options you could try, see this thread about a similar issue: [http://ubuntuforums.org/showthread.php?t=1784587](http://ubuntuforums.org/showthread.php?t=1784587)

Also note that the Linux kernel in 11.04 has some 'power issues' that might require the CPU to work harder and the fans be more noisy. However this should not result in constantly blazing fans.

---

