---
title: "Fan running constantly. Appears to be ATI graphics card issue..."
date: 2012-02-21
forum: General Help
---

### Post by big-ted on 2012-02-21
Hi all. OK, I've been trawling the web for help over the last few days, but to no avail, hence me starting a thread here.

Something recently got very messed up on my Ubuntu 10.04 system. Hardware is a Thinkpad T400 with ATI graphics card.

I've been having to boot in Windows a lot recently as I was doing some CAD work. I've finished with that now so it's back to Ubuntu. Speed seemed ok, but dragging windows and scrolling through documents was slow and jerky, to the point of intolerable. Eventually, I reinstalled the grflx package, which seemed to fix THAT issue. However, now my fan runs constantly. According to the thinkfan, app, 'sensor 3', which [http://www.thinkwiki.org/wiki/Thermal_Sensors#ThinkPad_T400](http://www.thinkwiki.org/wiki/Thermal_Sensors#ThinkPad_T400) suggests is the ATI graphics card (note that thinkfan indexes the sensors from zero) runs at about 50 degrees C. I'll be honest, I've no idea if this is something the fan should be coming on for. Ie: is it that the card is genuinely running hot, therefore the fan is coming on to prevent damage, or is it that the fan is coming on unnecessarily?

I've since grudgingly upgraded my OS to 10.10, with no change. Further, since re-installing the grflx package dual monitor support is a bit screwy, but I'll gladly deal with that if I can fix the constant drone of the fan!

The fan comes on about 60 seconds after start up.

Interestingly, setting all sensors to 'off' in thinkfan turns the fan off, but setting any ONE sensor to 'hw-ctrld' turns it on to about 3400 rpm. Presumably, hw-ctrld is 'hardware controlled'? Perhaps this is a bios issue? I DID edit the bios when I was having my original graphics issues. I will investigate this and update, but, in the meantime, any help appreciated!

---

### Post by big-ted on 2012-02-21
Hmm. Sure enough, setting bios to use integrated graphics solves the problem. To be fair, I don't KNOW that I was using the ATI card prior to editing the BIOS settings, but it sure seems like a waste now not to be able to use it. Still, it seems there are no shortage of threads discussing how to get the card itself working properly, so I'll mark this solved for now...

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-02-21
big-ted, take a look at this instruction:

[http://blogs.law.harvard.edu/djcp/2011/11/kubuntu-11-10-on-the-acer-aspire-timelinex-4830tg-6450/](http://blogs.law.harvard.edu/djcp/2011/11/kubuntu-11-10-on-the-acer-aspire-timelinex-4830tg-6450/)

It's a different piece of hardware, but the problem sounds same. One part of the solution is, as you discovered, switching to integrated graphics, as well as installing (and setting right) cpufreqd.

---

