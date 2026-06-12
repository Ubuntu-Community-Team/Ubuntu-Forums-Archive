---
title: "Ubuntu and Flash"
date: 2011-10-04
forum: General Help
---

### Post by garyjmellor on 2011-10-04
I'm trying to understand how Flash is working in Ubuntu. The version of Firefox I'm running atop Natty (7.0.1) has no issues with, for example, YouTube. I know (or thought I knew) that Ubuntu did not ship with Flash support. Have I misunderstood something or does it ship with Gnash...or is Flash support native in FF? The reason I ask is because I want to stop Flash (the Adobe kind if it is installed) as it, and sites that use it, can use so-called supercookies and I don't want them. I'd rather disable it or better still uninstall it and use Gnash instead. An explanation of how I'm able to play Flash format in FF on Natty would be good since I'm baffled as to how it's doing it without apparently shipping with Flash support. Thanks in advance.

---

### Post by collisionystm on 2011-10-04
When you installed the 'restricted-extras' flash came with it.

---

### Post by seawolf167 on 2011-10-04
Did you install the [Restricted Extras package]("https://help.ubuntu.com/community/RestrictedFormats")? This includes Flash for your system.

```
sudo apt-get install ubuntu-restricted-extras
```

I don't personally use GNU Gnash but I'm sure there are people out there that can help you with it. Their website is [here]("http://www.gnu.org/software/gnash/"), along with documentation [here]("http://www.gnu.org/software/gnash/documentation.html").

---

### Post by garyjmellor on 2011-10-04
In the words of Alan Partridge "Ah ha!" - yes, that would explain it. Thank you both for pointing out what should have been obvious to me. I'll check out the links.

---

### Post by viperdvman on 2011-10-04
Any particular reason you want to replace Flash, besides the supercookies? 

I only ask 'cause Flash runs poorly on my netbook when the ATI proprietary driver is installed, but totally fine with the ATI open-source driver.

---

### Post by lovinglinux on 2011-10-05
You can use [Flashblock](https://addons.mozilla.org/en-US/firefox/addon/433/) to prevent flash content from loading, so it will only save the cookies when you actually click the flash content.

You can also use [BetterPrivacy](https://addons.mozilla.org/en-US/firefox/addon/betterprivacy/) to delete those cookies.

---

