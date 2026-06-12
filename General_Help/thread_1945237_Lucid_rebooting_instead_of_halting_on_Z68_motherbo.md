---
title: "Lucid rebooting instead of halting on Z68 motherboard"
date: 2012-03-22
forum: General Help
---

### Post by CharlesA on 2012-03-22
Hello,

I've got a lucid x64 install that I moved from an old machine to a new i7 with a Z68 motherboard. If I try to shut it down using:

```
sudo halt
sudo poweroff
sudo shutdown -h now
```

It says it is halting/powering off/shutting down but doesn't power off. It reboots instead.

I have a feeling this is due to ACPI not being supported with Lucid, but I am not sure.

Any ideas?

EDIT: I ended up updating the BIOS and now it works perfectly fine.

The mobo in question is a Gigabyte Z68XP-UD3, which now has BIOS F9:
[http://www.gigabyte.us/products/product-page.aspx?pid=3892&dl=1#bios](http://www.gigabyte.us/products/product-page.aspx?pid=3892&dl=1#bios)

---

