---
title: "Xerox Phaser Duplex printing problem"
date: 2009-09-16
forum: General Help
---

### Post by apmcd47 on 2009-09-16
Linux:```
Distributor ID: Ubuntu
Description:    Ubuntu 8.04.3 LTS
Release:        8.04
Codename:       hardy

```Cups version 1.3; Xerox Phaser 7400DT.

This printer is Duplex-Long-Edge by default.

If I *2-up* a PS file with *psnup* and then try to print it either using *kprinter* or *lp/lpr* it comes out simplex mode. If I try, e.g.
```
lpr -o sides=two-sided-short-edge myfile.ps
```
I get the same result. *2-up-ing* using the K printer interface has the same result (it uses *psnup*?). If I don't *2-up* a file I can change the Duplex mode as I see fit. I don't have the same problems with other printers, but on the other hand only the Xerox PPD files have things like:
```
*Duplex DuplexNoTumble/Long-Edge Binding: "
   <</Duplex true /Tumble false>> xerox$pagedevice copy pop
"

```
It's more likely to be:
```
<</Duplex true /Tumble false>> setpagedevice
```

Unfortunately using other printers will not be an option.

Can anyone help, either by having a fix, or by suggesting where I look on the system to further investigate this? Or maybe it's a known problem?

I would be grateful for all assistance.

Andrew

---

