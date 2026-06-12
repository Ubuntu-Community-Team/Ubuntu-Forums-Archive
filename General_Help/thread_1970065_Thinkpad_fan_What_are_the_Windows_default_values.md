---
title: "Thinkpad fan: What are the Windows default values?"
date: 2012-04-30
forum: General Help
---

### Post by sbw87 on 2012-04-30
Hi there,

I'm using a Thinkpad X1 and Ubuntu 12.04. I have enabled Thinkfan in order to reduce the noise level produced by the system fan. However, the fan can still be heard when executing light tasks such as watching flash video, making Skype calls etc.

I know that the fan level chosen is dependent on the exact Thinkfan settings in thinkfan.conf. Also, of course this is a trade-off between noise levels and system stability...

Therefore, does anyone of you know the default values used to control the fan of such a Thinkpad under the factory-default Windows installation? I'd like to use the same values if possible, in order to have a relatively silent laptop while not putting my system at risk.

Many thanks!

---

### Post by tnagya on 2012-05-01
Hi there!
I think the factory Windows default is the Bios default, which is used by Ubuntu by default too. In my system (ThinkPad Z61m) When installing Ubuntu it somehow stresses the system more than Windows, that's why the louder noise from the fan. I guess it is some kind of kernel-power-saving issue, or something.

There are several workarounds on that, but if you want to get a more silent PC in Ubuntu, you have to allow higher levels of temperature by _overriding_ the factory defaults. (Ie. You won't get a silent Ubuntu with factory defaults)
Here is a nice [link]("http://solutionlocker.wordpress.com/2012/04/02/installing-ubuntu-12-04-on-thinkpad-x121e-i3-fan-noise/").
For Windows use: [here]("http://www.staff.uni-marburg.de/%7Eschmitzr/donate.html")

On my machine I scale down my CPU and video card to a minimum and I set the programs to turn on fan when temp reaches 64Celsius. Which is about 15 more than the factory settings I guess. However This is an old (4 years+) laptop, and I dare messing around with it. With that 64C I can get a constantly silent machine on Windows without turning the fan on (I have SSD) when doing light tasks. And a quite silent on Ubuntu (fan sometimes turns on) Light tasks are: Browsing, pdf-reading, etc. However please note, that Flash playing is not a light task.

Summary: You won't get a silent laptop without putting your computer to risk.
Epilogue: When there is no fan or hdd making noise in my machine I can sometimes hear the pitching noise from my video card... Sucks

---

