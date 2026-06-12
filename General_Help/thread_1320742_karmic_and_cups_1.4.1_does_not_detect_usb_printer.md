---
title: "karmic and cups 1.4.1 does not detect usb printer"
date: 2009-11-09
forum: General Help
---

### Post by fivenote on 2009-11-09
I connect a Canon BJ-200 to usb using a parallel/usb adapter cable.

This has worked fine with ubuntu versions up through jaunty. With karmic (both upgrades and fresh installs), cups does not detect my printer.

After searching a bit on the issue, I see some have detection issues with some usb-connected printers. I was able to get a newer usb printer connected, but not my old bj-200. 

On newer printers, I see them detected by the kernel under /dev/usb/lp0 and by cups by running "lpinfo -v". With the BJ-200, I see it under /dev/usb/lp0, but not under "lpinfo -v". 

How do I get my BJ-200 connected?

Thanks for any help.

---

### Post by fivenote on 2009-11-09
SOLVED

cups 1.4.1 has new usb handling and doesn't see my canon bj-200e as a usb printer since it's a parallel printer with a parallel-to-usb cable.

This bug report gave me the answer...

[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/436495](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/436495)

I needed to specify the URI as 
```
parallel:/dev/usb/lp0
```
not
```
usb:/dev/usb/lp0
```

This was not easy to find, nor documented anywhere else as far as I could tell. I hope this helps others who are still connecting their old parallel printers to usb ports.

---

### Post by GrantsV on 2009-11-10
Thanks, thats got it for my Dell 3110CN that is undetectable in Karmic!

---

### Post by UN-BE-LIEV-ABLE Zenyatta! on 2009-11-10
I signed up specially to say THANK YOU. :D
  
Got my old HP 4050 churning out the goods again!

---

