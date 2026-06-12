---
title: "Poor Battery Life in 12.04"
date: 2012-05-30
forum: General Help
---

### Post by Kreeyon on 2012-05-30
I am using a Dell XPS M1330 and have upgraded to ubuntu 12.04 hoping that the power issues have been improved but have found them to be the same as in 11.10.

I have a brand new 9 cell battery installed that I can easily get around 4 to 5 hours of use from Windows 7 through light web browsing and using office and email.  However, on Ubuntu on a fully charged battery as soon as I remove the power cord the battery meter drops to orange and tells me I have only 2 hours remaining.  If I start doing anything like opening applications or browsing the internet this starts to drop even further to just over an hour and a half.

I have the screen brightness down to a point were I can barely see the screen and this will give my an extra half an hour

What's going on with Ubuntu and laptop batteries??

---

### Post by 2F4U on 2012-05-30
My suggestion would be that you take a look at TLP:

[http://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html](http://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html)

This is a set of scripts intended to tweak laptop power management settings. While originally developed for ThinkPad notebooks, the majority of settings applies to other models too.

---

### Post by philinux on 2012-05-30
> **Kreeyon said:**
> I am using a Dell XPS M1330 and have upgraded to ubuntu 12.04 hoping that the power issues have been improved but have found them to be the same as in 11.10.

I have a brand new 9 cell battery installed that I can easily get around 4 to 5 hours of use from Windows 7 through light web browsing and using office and email.  However, on Ubuntu on a fully charged battery as soon as I remove the power cord the battery meter drops to orange and tells me I have only 2 hours remaining.  If I start doing anything like opening applications or browsing the internet this starts to drop even further to just over an hour and a half.

I have the screen brightness down to a point were I can barely see the screen and this will give my an extra half an hour

What's going on with Ubuntu and laptop batteries??

My Acer 1410 behaves normally. I get 5 to 6 hours using ubuntu. Same as Win 7. This is with brightness turned down in both cases.

You might like to try Jupiter. > It is designed to improve battery life of a portable Linux computer by integrating with the operating system and changing parameters of the computer based on battery or powered connection.

[http://www.ubuntugeek.com/jupiter-light-weight-power-and-hardware-control-applet.html](http://www.ubuntugeek.com/jupiter-light-weight-power-and-hardware-control-applet.html)

---

### Post by Kreeyon on 2012-05-31
Thanks.

Iv'e followed the suggestions above but only makes a marginal difference.

After some research I decided to calibrate the battery in Ubuntu by disabling Ubuntu from shutting down the laptop when the battery is critically low and allow the battery to run down to 0, then charge the battery to 100% from within Ubuntu.  Doing this a couple of times and having Jupiter running in the background has made a massive difference to battery life.  Eventhough still not as good as what I can get in Windows 7, I am now achieving 4 hours of life during light use.

---

### Post by friTTe81 on 2012-05-31
> **2F4U said:**
> My suggestion would be that you take a look at TLP:

[http://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html](http://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html)

This is a set of scripts intended to tweak laptop power management settings. While originally developed for ThinkPad notebooks, the majority of settings applies to other models too.

Thanks for the info :)

---

### Post by friTTe81 on 2012-05-31
> **Kreeyon said:**
> Thanks.

Iv'e followed the suggestions above but only makes a marginal difference.

After some research I decided to calibrate the battery in Ubuntu by disabling Ubuntu from shutting down the laptop when the battery is critically low and allow the battery to run down to 0, then charge the battery to 100% from within Ubuntu.  Doing this a couple of times and having Jupiter running in the background has made a massive difference to battery life.  Eventhough still not as good as what I can get in Windows 7, I am now achieving 4 hours of life during light use.

Might be trying that calibrating myself, noticed more diff?

---

### Post by Kreeyon on 2012-06-04
It does seem to have given me a bit more life but it's really hard to tell.  The battery still seems to be draining way quicker than in Windows

---

### Post by gordintoronto on 2012-06-04
What settings did you pick in Jupiter? It's not automatic!

---

### Post by Kreeyon on 2012-06-05
Power Saving Settings have been applied in Jupiter.

---

