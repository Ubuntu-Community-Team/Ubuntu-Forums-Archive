---
title: "IE in Linux"
date: 2012-03-16
forum: General Help
---

### Post by Orcris on 2012-03-16
I need IE to test websites, since it's still the third most used browser. Is there any way to install IE in Linux?

---

### Post by Habitual on 2012-03-16
wine, or virtualbox

---

### Post by yetiman64 on 2012-03-16
Older versions may be possible to run under Wine, but I suspect that won't meet your needs.

Another suggestion is to do a virtual machine install of Windows (if you have the relevant Windows licence - not OEM), personally I like Virtualbox, there is VMWare as well.

This would allow you to run IE natively in Windows, after booting into Ubuntu. In case you are not familiar with virtualization, you would be effectively running the 2 operating systems at the same time on the same hardware, so your hardware would need to have sufficient resources and support for virtualization enabled in BIOS (the AMD-V or Intel-VT settings need to be enabled).

About the only thing that doesn't run well in a virtualized Windows install is DirectX. There is experimental support for it but it can be flaky at times. This really only affects gaming usually.

---

### Post by OGpmpdog on 2012-03-16
Most of us started using Linux because of whatever hangups we have with MS.:lolflag:

I dont know if IE will run in Linux...maybe you could run either Windows or Linux in a secondary VM?

IE could be an option, but, in Linux, Chrome, Opera, Aurora, Epiphany, and, FF, of course, are options too.

Good Luck.

---

### Post by 3Miro on 2012-03-16
Wine comes with a browser that is supposed to emulate IE. I doubt any real version of IE can be installed under wine.

---

### Post by yetiman64 on 2012-03-16
> **3Miro said:**
> .... I doubt any real version of IE can be installed under wine.
Yes, I'd agree. I have seen instructions for installing older versions of IE (versions 4,5 or 6) in Wine, but nowadays that would be pretty pointless and insecure at best. :)

---

### Post by jim_deadlock on 2012-03-17
Other options:

[http://netrenderer.com/]("http://netrenderer.com/") (free)
[http://crossbrowsertesting.com/]("http://crossbrowsertesting.com/") ($$)

---

### Post by Mark Phelps on 2012-03-18
> I need IE to test websites

Then, put simply, you're using the wrong OS.

I've seen claims that some folks have been able to install IE all the way up to version 8 (!!) -- which, for IE development and testing, is useless.

Much of the MS community uses IE 9.x now, and 10.x is already out in preview form in Win8CP.

Using Linux to test IE development would be like saying you're developing for Firefox but the latest version your OS support is version 3.x -- when v11 is already out.

---

